# 도쿄 여행 가계부

친구들과 링크 하나로 함께 적고 바로 정산하는 여행 가계부입니다.
GitHub Pages(화면) + Supabase(저장소)로 동작하며, 링크를 받은 사람은 가입 없이 사용할 수 있습니다.

## 폴더 구성

- `index.html`: 앱 화면 전체 (이 파일 하나로 동작)
- `supabase/setup.sql`: Supabase 데이터베이스 설정 스크립트
- `.gitignore`: 올리지 않을 파일 목록

## 설정 순서

1. Supabase에서 새 프로젝트를 만들고, SQL Editor에 `supabase/setup.sql` 전체를 붙여 넣어 Run 합니다.
2. Project Settings > API 에서 Project URL과 anon public 키를 복사합니다.
3. `index.html` 아래쪽 `SUPABASE_URL`, `SUPABASE_KEY` 두 줄에 붙여 넣습니다.
4. 이 폴더를 GitHub 저장소(Public)에 올리고, Settings > Pages 에서 Branch를 `main` / `/(root)`로 저장합니다.
5. 잠시 뒤 `https://<아이디>.github.io/tokyo-trip-ledger/` 주소로 접속합니다.

## 정산 계산 방법

- 원화 환산: 현지 통화 금액 × 기준환율 (엔화는 ÷ 100)
- 1인 부담: 지출별 원화 환산액 ÷ 나누는 인원
- 차액: 낸 돈 − 쓴 몫 (플러스는 받을 돈, 마이너스는 보낼 돈)
- 송금: 송금 건수가 최소가 되도록 큰 금액부터 연결, 원 단위 반올림

## 보안 메모

- anon 키는 공개되어도 되는 키입니다. 테이블 직접 접근은 막혀 있고, 여행 ID(UUID)를 아는 경우에만 읽고 쓸 수 있습니다.
- 여행 링크를 받은 사람은 그 여행을 수정·삭제할 수 있으니 링크는 함께 여행하는 사람끼리만 공유하세요.
- `service_role` 키는 절대 `index.html`에 넣지 마세요.
