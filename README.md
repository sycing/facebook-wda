# python-wda
[![Build Status](https://travis-ci.org/codeskyblue/python-wda.svg?branch=master)](https://travis-ci.org/codeskyblue/python-wda)

Facebook WebDriverAgent Python Client Library (not official)

Not finished yet.

## Installation
1. You need to start WebDriverAgent by yourself

	Follow the instructions in <https://github.com/facebook/WebDriverAgent>

	And start WDA with command

	```
	xcodebuild -project WebDriverAgent.xcodeproj -scheme WebDriverAgentRunner -destination 'platform=iOS Simulator,name=iPhone 6' test
	```

2. Install python wda client

	```
	pip install --pre facebook-wda
	```

## How to use
```
import wda

c = wda.Client('http://localhost:8100')
print c.status()
c.screenshot('screen.png')
c.home()

s = c.session('com.apple.Health')
print s.orientation # expect PORTRAIT
print s.window_size
s.tap(200, 200)
print s(text="Dashboard").elements
# not working function
# s(text="Dashboard").tap()
s.close() # kill app
```

## Wired Problem
```
s(text="Dashboard").tap()
```
is not working.

What I get the element id is a very long string, like this.

```
{u'label': u'Dashboard', u'type': u'XCUIElementTypeStaticText', u'ELEMENT': u'FDFA10CA-4E13-431A-8199-8AD1ADDB4AF2'}
```

But when I follow the instructions in WDA Repository README

```
curl -X POST -d "" $DEVICE_URL/session/$SESSION_ID/element/FDFA10CA-4E13-431A-8199-8AD1ADDB4AF2/click
```

Nothing happends. Need help

## iOS Build-in Apps
|   Name | Bundle ID          |
|--------|--------------------|
| iMovie | com.apple.iMovie |
| Chrome | com.google.chrome.ios |
| Apple Store | com.apple.AppStore |
| Weather | com.apple.weather |
| Camera | com.apple.camera |
| iBooks | com.apple.iBooks |
| Health | com.apple.Health |
| Desktop | com.apple.springboard |

## Reference
[Source code](https://github.com/facebook/WebDriverAgent/blob/master/WebDriverAgentLib/Commands/FBElementCommands.m#L62)
 
## DESIGN
[DESIGN](DESIGN.md)

## LICENSE
[MIT](LICENSE)
