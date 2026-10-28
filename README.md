# 토끼굴 (Rabbit Hole)

국내 이북 리더기(크레마 모티프·크레마S·오닉스 Boox)를 위한 가벼운 안드로이드 웹브라우저.
[EinkBro](https://github.com/plateaukao/einkbro) 에서 갈라져 나온 포크이며, 이시로스튜디오가 유지한다.

> 아직 개발 중이다. 첫 릴리스 전까지는 원본 EinkBro 와 같은 앱이다.

## 왜 포크인가

EinkBro 는 전자잉크용 브라우저로서 완성도가 높지만, AI 대화·클라우드 동기화·유저스크립트·번역·TTS 처럼
이북 리더기에서 쓸 일이 없는 기능이 설정 화면을 채운다. 토끼굴은 반대로 간다.

- **덜어낸다.** 외부 API 키가 필요한 기능과 서비스 의존 기능은 코드째 뺀다.
- **기본값으로 켠다.** 페이지 넘김, 큰 글꼴, 굵은 글씨, 광고 차단, 한글 폰트는 설치 직후부터 켜져 있다.
- **한국 사용자에 맞춘다.** 네이버·다음 검색, 국내 광고 필터, 한글 줄바꿈(`word-break: keep-all`), 한국어·영어 두 언어만.
- **설정은 한 화면.** 글꼴, 페이지 넘김, 검색엔진, 광고 차단, 이미지, 백업. 그 이상은 만들지 않는다.

자세한 기획은 `docs/plan.md` 에 둔다(작성 예정).

## 대상 기기

| 기기 | 안드로이드 | 설치 방법 |
| --- | --- | --- |
| 크레마 모티프 | 11 | APK 직접 설치 (플레이 스토어 없음) |
| 크레마S | 10 | APK 직접 설치 |
| 오닉스 Boox (Poke·Leaf·Go·Palma·Note) | 11 이상 | APK 직접 설치 또는 F-Droid |
| 리디페이퍼 | — | 지원하지 않음 (앱 설치가 막혀 있음) |

최소 안드로이드 7.0 (API 24). 기기 내장 WebView 를 쓰므로 WebView 가 오래된 기기에서는 일부 사이트가 열리지 않을 수 있다.

## 받기

GitHub Releases 에서 APK 를 받아 설치한다. 플레이 스토어에는 올리지 않는다.
(릴리스 전까지는 Actions 의 빌드 산출물만 있다.)

## 빌드

```bash
./gradlew assembleDebug          # 디버그 APK
./gradlew testDebugUnitTest      # 단위 테스트
./gradlew lintDebug              # 린트
```

JDK 17, Android SDK 36 이 필요하다. 그 밖의 명령은 `docs/upstream/CLAUDE.md` (원본 안내) 참고.

## 라이선스와 출처

- 이 프로그램은 [GNU GPL v3 또는 그 이후 버전](LICENSE.md)으로 배포된다. 소스를 고쳐 배포할 때는 같은 라이선스로 소스를 공개해야 한다.
- 원본: [EinkBro](https://github.com/plateaukao/einkbro) (Daniel Kao 외 기여자, GPL-3.0-or-later). 그 원본은 [FOSS Browser](https://codeberg.org/Gaukler_Faun/FOSS_Browser) 에서 갈라져 나왔다.
- 포크 기준: EinkBro v16.7.1, 커밋 `03632653` (2026-10-28). 그 뒤의 변경은 [CHANGELOG.md](CHANGELOG.md) 에 적는다.
- 기여자 목록은 [CONTRIBUTORS.md](CONTRIBUTORS.md), 원본 문서는 `docs/upstream/` 에 그대로 보관한다.
- 이 저장소는 자유·오픈소스 소프트웨어(FOSS) 규칙을 지킨다: 비공개 SDK·추적기·광고를 넣지 않고, 의존성은 전부 오픈소스 라이선스여야 한다.

## 운영

- 배포: GitHub Releases 에 APK 첨부. 태그 `vX.Y.Z`, `CHANGELOG.md` 맨 위 한 줄.
- 보안 수정은 원본 EinkBro 의 커밋을 골라 가져온다(`git cherry-pick`). 기능 추가는 따라가지 않는다.
- 빌드 체인(Gradle·Kotlin·Compose) 버전은 연 1회만 올린다. 올리기 전에 `./gradlew testDebugUnitTest` 가 통과하는지 본다.
- 문의: shiroleestudio@gmail.com
