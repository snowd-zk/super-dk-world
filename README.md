# 🍄 SUPER DK WORLD (슈퍼 DK 월드) - 갤럭시 탭 맞춤형 마리오 게임

> **Executive Summary (3줄 핵심 요약)**  
> 1. 만 6세 남아(DK)를 위해 아빠가 제작한 **PWA 기반 HTML5 60fps 정통 2D 플랫포머(`SUPER DK WORLD`)**이다.  
> 2. 갤럭시 탭 가로 모드 터치스크린에 최적화된 **130% 확장 히트박스, 코요테 타임(120ms), 점프 버퍼링(150ms)**으로 소근육 오조작 스트레스를 방지한다.  
> 3. [영재 심리 육아법](file:///Users/SD/Documents/SD_Project/DK/00_%EA%B8%B0%EB%B3%B8%EC%A0%95%EB%B3%B4_%EB%B0%8F_%EC%B2%A0%ED%95%99/gifted_parenting_memory.md)을 적용하여, 정통 Game Over 후 **원터치 체크포인트 이어하기와 상황별 과정 칭찬 코칭 카드**를 제공한다.

---

## 📌 1. 파일 구성 및 실행 방법

- **메인 실행 파일**: [`index.html`](file:///Users/SD/Documents/SD_Project/DK/03_%EA%B5%90%EC%9C%A1_%EB%B0%8F_%ED%95%99%EC%8A%B5/super_dk_world/index.html)
- **PWA 매니페스트**: [`manifest.json`](file:///Users/SD/Documents/SD_Project/DK/03_%EA%B5%90%EC%9C%A1_%EB%B0%8F_%ED%95%99%EC%8A%B5/super_dk_world/manifest.json)
- **오프라인 서비스 워커**: [`sw.js`](file:///Users/SD/Documents/SD_Project/DK/03_%EA%B5%90%EC%9C%A1_%EB%B0%8F_%ED%95%99%EC%8A%B5/super_dk_world/sw.js)
- **앱 아이콘**: [`icon.svg`](file:///Users/SD/Documents/SD_Project/DK/03_%EA%B5%90%EC%9C%A1_%EB%B0%8F_%ED%95%99%EC%8A%B5/super_dk_world/icon.svg), [`icon-192.png`](file:///Users/SD/Documents/SD_Project/DK/03_%EA%B5%90%EC%9C%A1_%EB%B0%8F_%ED%95%99%EC%8A%B5/super_dk_world/icon-192.png), [`icon-512.png`](file:///Users/SD/Documents/SD_Project/DK/03_%EA%B5%90%EC%9C%A1_%EB%B0%8F_%ED%95%99%EC%8A%B5/super_dk_world/icon-512.png)
- **기획 마스터 플랜**: [`super_dk_mario_game_plan.md`](file:///Users/SD/Documents/SD_Project/DK/03_%EA%B5%90%EC%9C%A1_%EB%B0%8F_%ED%95%99%EC%8A%B5/super_dk_mario_game_plan.md)

### 📱 삼성 갤럭시 탭 홈 화면 설치 방법 (PWA 전체화면)
1. 로컬 폴더에서 정적 서버를 실행하거나 호스팅 URL을 갤럭시 탭 브라우저(Samsung Internet 또는 Chrome)로 접속한다.
2. 브라우저 메뉴에서 **[홈 화면에 추가 (Add to Home screen)]**를 선택한다.
3. 홈 화면에 생성된 **`[슈퍼 DK 월드]`** 아이콘을 터치하면 주소창 없는 가로 모드 전체화면(`standalone`, `landscape`)으로 즉시 구동한다.

### 💻 PC / Mac 즉시 테스트 방법
- Finder에서 [`index.html`](file:///Users/SD/Documents/SD_Project/DK/03_%EA%B5%90%EC%9C%A1_%EB%B0%8F_%ED%95%99%EC%8A%B5/super_dk_world/index.html)을 더블클릭하면 외부 인터넷 연결 없이 즉시 실행한다.
- **키보드 조작**:
  - 이동: `◀` / `▶` 또는 `A` / `D`
  - 점프: `Space`, `▲`, `W`, `Z`
  - 파이어볼 발사(파이어 DK 변신 시): `X`, `F`, `Shift`

---

## 🎮 2. 핵심 게임 메커니즘 (Phase 1 ~ Phase 5 완전 구현)

### 2.1 소근육 배려 3대 비밀 물리 보정 (Secret Assist Physics)
- **코요테 타임 (Coyote Time, 120ms)**: 절벽 끝을 벗어난 직후 0.12초 안에 점프 버튼을 눌러도 정상 점프가 발동한다.
- **점프 버퍼링 (Jump Buffering, 150ms)**: 착지 직전 0.15초 전에 점프를 미리 눌러도 바닥에 닿는 즉시 다음 점프가 나간다.
- **관대한 히트박스 (Forgiving Hitbox)**: 몬스터를 위에서 밟는 판정은 120%로 넓히고, 옆에서 부딪히는 피격 판정은 중심부 75%로 좁혀 억울한 실수를 줄인다.

### 2.2 '슈퍼 DK' 3단 변신 및 무적 스타
1. **꼬마 DK (기본)**: 빠르고 날렵한 기본 상태이다.
2. **슈퍼 DK (슈퍼버섯 🍄)**: 키가 1.5배 커지며 일반 벽돌을 머리로 부술 수 있다. 적과 부딪혀도 생명을 잃지 않고 꼬마 DK로 돌아간다.
3. **파이어 DK (파이어플라워 🔥)**: 하얀 모자와 붉은 코스튬으로 변신하며, 우측 하단에 전용 **`[🔥 불꽃(B)]`** 터치 버튼이 활성화된다.
4. **무적 스타 (슈퍼스타 ⭐)**: 10초 동안 무지개 빛 파티클을 뿜으며 닿는 모든 적을 즉시 물리친다.

### 2.3 4대 테마 월드 및 대마왕 쿠파 보스전
- **World 1-1 (햇살 초원)**: 기본 점프와 물음표 블록, 토관, 계단 지형을 익히며 스타코인 3개를 수집한다.
- **World 1-2 (신비한 지하 동굴)**: 푸른 벽돌 천장 위 숨겨진 비밀 통로를 탐색하고 파이어볼로 적 편대를 물리친다.
- **World 1-3 (구름 다리 하늘길)**: 움직이는 구름 엘리베이터와 고탄성 점프대(스프링)를 활용해 하늘 다리를 건넌다.
- **World 1-4 (대마왕 쿠파 성)**: 회전 불꽃 막대를 넘어 대마왕 쿠파와 맞선다. **파이어볼 5회 명중** 또는 쿠파가 점프할 때 아래로 통과해 **황금 도끼(Axe)를 터치하여 다리를 무너뜨리는** 2가지 클리어 방식을 지원한다.

---

## 🧠 3. 영재 심리 회복탄력성(Resilience) 코칭 연계

생명 3개를 모두 소진해 `GAME OVER`가 발생해도 **World 1-1로 강제 초기화하지 않는다.** 지금까지 모은 스타코인과 해금된 월드는 `localStorage`에 안전하게 유지하며, 실패 원인(낙사 / 몬스터 충돌 / 보스전)에 맞춘 **전략 힌트와 과정 칭찬 카드**를 띄운 뒤 체크포인트에서 생명 3개를 충전해 즉시 재도전하도록 돕는다.
