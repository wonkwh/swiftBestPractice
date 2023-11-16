# swift-style-guide

- ncn ios team 사용하는 `swift` 언어의 style-guide, xcode 셋팅, lint config file, format config file을 공유
- [SwiftStyleGuide](SwiftStyleGuide.md) 에 자세히 설명한다. 

## Getting started

```sh
  brew install swiftlint
  brew install swift-format
```

- formatter 로 애플의 `swift-format`  을 사용한다.  `SwiftFormat` 과 햇갈리지 말자  

## Xcode Settings
- Project setting -> Text Setting에서 Spaces, Width의 Tab 2, Indent 2로
- Xcode 설정에서  Text Editing ▸ Editing  선택후 Including whitespace-only lines 을 체크

![](https://github.com/kodecocodes/swift-style-guide/blob/main/screens/trailing-whitespace.png?raw=true)

## Running SwiftLint

To simplify the process for everyone in the content pipeline, you'll need to add the necessary instructions to your sample project to run SwiftLint automatically on each build. To do so:

1. Select the project document in the Project navigator.
1. Select the **Build Phases** tab.
1. Click **+** and choose **New Run Script Phase**.

![](https://github.com/kodecocodes/swift-style-guide/blob/main/screens/add-run-script.png?raw=true)

4. Drag the new phase before the **Compile Sources** phase.
4. Click the disclosure triangle on the **Run Script** phase and ensure **Shell** is set to **/bin/sh**.

![](https://github.com/kodecocodes/swift-style-guide/blob/main/screens/empty-run-script.png?raw=true)

6. Add the following script:
```
PATH=/opt/homebrew/bin:$PATH
if [ -f ~/ncn.swiftlint.yml ]; then
  if which swiftlint >/dev/null; then
    swiftlint --no-cache --config ~/ncn.swiftlint.yml
  fi
fi
```

## Link

### format 관련
- https://github.com/apple/swift-format
- https://swift-format.com/
	- format config 파일을 미리보기 할 수 있다
- https://exyte.com/blog/how-to-start-working-with-swift-format

### lint 관련
- https://realm.github.io/SwiftLint/
- https://github.com/kodecocodes/swift-style-guide
- https://ricardojpsantos.medium.com/using-swiftlint-to-decrease-code-smell-on-xcode-e1dd49258f22

