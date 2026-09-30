# chagok-app-policy

차곡차곡 앱의 이용약관·개인정보 처리방침을 Netlify로 게시한다(`publish` 브랜치 → `https://chagok-app-terms.netlify.app`).
앱은 `https://chagok-app-terms.netlify.app/{terms,privacy}/`를 앱 안 시트로 열고,
로그인한 사용자의 재동의 판단에 `versions.json`을 읽는다.

## 개정하는 방법

1. `terms/v2/index.html`처럼 새 판 폴더를 만든다. 이미 시행된 판의 본문은 고치지 않는다(오탈자만).
2. `versions.json`에 판을 추가한다. `postedAt`(게시일)과 `effectiveAt`(시행일)은 로컬 날짜 `YYYY-MM-DD`.
   - 사전 고지: 시행일 7일 전, 이용자에게 불리하면 30일 전에 게시한다.
   - `requiresConsent`: 로그인한 사용자에게 다시 동의를 받을 개정이면 `true`.
3. 시행일 전까지 `terms/`는 이전 판을 보여주고 위에 "M월 D일부터 바뀌어요"를 띄운다.
   판 선택 규칙은 앱의 `src/policy/versions.ts`와 같다.

## 게시 전 채울 것

`[문의 이메일]`, `[클라우드 사업자]`, 판 날짜. 최종 문안은 법률 검토를 받는다.

## 게시

Netlify는 `publish` 브랜치만 배포한다. 지금 `publish`에는 "준비 중" 페이지만 있다.
빈칸을 채운 `main`을 `publish`에 반영하면(또는 Netlify 운영 브랜치를 `main`으로 바꾸면) 게시된다.
