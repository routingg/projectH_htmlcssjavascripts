# Journey to Gate

JDC 공공데이터가 제주 여행의 탐색, 일정, 공항 이동, 면세점 탐색, Gate 이동으로 이어지는 방식을 보여 주는 데스크톱 우선 서비스 프로토타입입니다.

## Service Concept

**제주 여행의 시작부터 Gate까지.**

공공데이터를 단순 조회하는 대신, 사용자의 선택을 다음 의사결정과 경험으로 연결하는 `PUBLIC DATA → DECISION → JOURNEY` 구조를 제안합니다.

## File Structure

```
index.html             SPA markup
styles.css             design tokens, layout, responsive and a11y styles
app.js                 state, rendering, interaction and localStorage
data/destinations.js   local travel destination demo data
data/jdc-stores.js     local JDC-shopping-shaped demo data
data/airport.js        airport demo scenario
data/data-sources.js   Data Trace metadata
```

## How to Run

`index.html`을 더블클릭하여 브라우저에서 열면 됩니다. `file://` 환경에서 실행되며 서버, 빌드 과정, 네트워크 연결이 필요하지 않습니다.

## Technology

HTML5, CSS3, Vanilla JavaScript만 사용합니다. 외부 CDN, 폰트, 이미지, 프레임워크, npm 패키지 및 API 호출은 없습니다.

## Current Data Mode

**Prototype / Demo Local Dataset**입니다. 여행지, 매장, 공항 시간, 지도 좌표 및 쇼핑 동선은 모두 UX 검증을 위한 가상 데이터·스키매틱이며 실제 운영 정보가 아닙니다.

## No API Yet

현재 API 연결은 없습니다. 코드에 `fetch`, axios 또는 숨은 네트워크 의존성이 없습니다.

## Future Integration

- JDC OpenAPI 매장 정보
- 실제 관광 공공데이터
- 공항 운영/항공편 데이터
- 위치 및 경로 데이터

## API Adapter Change Points

실제 API를 연결할 때 다음만 교체하거나 확장하면 UI를 유지할 수 있습니다.

- `data/destinations.js`의 `window.DESTINATIONS` → 관광 데이터 어댑터 결과
- `data/jdc-stores.js`의 `window.JDC_STORES` → JDC API 어댑터 결과
- `data/airport.js`의 `window.AIRPORT` → 공항 데이터 어댑터 결과
- `data/data-sources.js`의 출처/현재 상태 메타데이터
- `app.js`의 `dataService.getDestinations()`와 `dataService.getJdcStores()`만 실제 비동기 데이터 제공 방식에 맞게 교체

Data Trace는 위 메타데이터를 읽으므로, 연결 상태와 데이터셋 설명도 함께 최신화해야 합니다.

## Important Limitation

데모 데이터는 실제 영업정보, 재고, 실시간 항공편, 실제 이동 시간, 실제 공항 좌표 또는 접근성 보장을 의미하지 않습니다.
