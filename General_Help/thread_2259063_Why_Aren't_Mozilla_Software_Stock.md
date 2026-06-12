---
title: "Why Aren't Mozilla Software Stock"
date: 2015-01-01
forum: General Help
---

### Post by KitchM on 2015-01-01
As a new user of Xubuntu, I was surprised to see the odd behavior of Thunderbird and Firefox.  I've used them for many years and only on this distro did they not perform as expected.  Why does Ubuntu "tweak" them?  How can one get the plain, stock versions?

---

### Post by whitesmith on 2015-01-01
Can you help us help you by posing specific differences?

---

### Post by slickymaster on 2015-01-01
> **tech-frontrowcomputer said:**
> As a new user of Xubuntu, I was surprised to see the odd behavior of Thunderbird and Firefox.  I've used them for many years and only on this distro did they not perform as expected.  <---snip--->

What exactly do you mean by "... odd behavior..." and "... not perform as expected."?

---

### Post by KitchM on 2015-01-01
I'm glad you all asked.  Here's a quicky list.

The junk mail will not move automatically to the junk box as requested.  The error console has lots of odd messages, such as:

Could not read chrome manifest 'file:///usr/lib/thunderbird/extensions/%7B972ce4c6-7e08-4474-a285-3208198ce6fd%7D/chrome.manifest'.

```
Timestamp: 15-01-01 05:13:10 PM
Warning: mutating the [[Prototype]] of an object will cause your code to run very slowly; instead create the object with the correct initial [[Prototype]] value using Object.create
Source File: resource://gre/modules/Preferences.jsm
Line: 378

Timestamp: 15-01-01 05:13:11 PM
Warning: mutating the [[Prototype]] of an object will cause your code to run very slowly; instead create the object with the correct initial [[Prototype]] value using Object.create
Source File: resource://gre/components/steelApplication.js
Line: 783

Thu Jan 01 2015 17:13:13 GMT-0500 (EST) CH: Current logLevel: 1

Timestamp: 15-01-01 05:13:15 PM
Warning: Unknown property 'margin-end'.  Declaration dropped.
Source File: [https://mozorg.cdn.mozilla.net/media/css/thunderbird-start-min.css?build=305192a](https://mozorg.cdn.mozilla.net/media/css/thunderbird-start-min.css?build=305192a)
Line: 1, Column: 2674
Source Code:
@font-face{font-family:'Open Sans Light';src:url('/media/fonts/OpenSans-Light-webfont.eot?#iefix') format('embedded-opentype'),url('/media/fonts/OpenSans-Light-webfont.woff') format('woff'),url('/media/fonts/OpenSans-Light-webfont.ttf') format('truetype');font-weight:normal;font-style:normal}@font-face{font-family:'Open Sans Light';src:url('/media/fonts/OpenSans-Semibold-webfont.eot?#iefix') format('embedded-opentype'),url('/media/fonts/OpenSans-Semibold-webfont.woff') format('woff'),url('/media/fonts/OpenSans-Semibold-webfont.ttf') format('truetype');font-weight:bold;font-style:normal}@font-face{font-family:'Open Sans Light';src:url('/media/fonts/OpenSans-LightItalic-webfont.eot?#iefix') format('embedded-opentype'),url('/media/fonts/OpenSans-LightItalic-webfont.woff') format('woff'),url('/media/fonts/OpenSans-LightItalic-webfont.ttf') format('truetype');font-weight:normal;font-style:italic}@font-face{font-family:'Open Sans';src:url('/media/fonts/OpenSans-Regular-webfont.eot?#iefix') format('embedded-opentype'),url('/media/fonts/OpenSans-Regular-webfont.woff') format('woff'),url('/media/fonts/OpenSans-Regular-webfont.ttf') format('truetype');font-weight:normal;font-style:normal}@font-face{font-family:'Open Sans';src:url('/media/fonts/OpenSans-Bold-webfont.eot?#iefix') format('embedded-opentype'),url('/media/fonts/OpenSans-Bold-webfont.woff') format('woff'),url('/media/fonts/OpenSans-Bold-webfont.ttf') format('truetype');font-weight:bold;font-style:normal}@font-face{font-family:'Open Sans';src:url('/media/fonts/OpenSans-Italic-webfont.eot?#iefix') format('embedded-opentype'),url('/media/fonts/OpenSans-Italic-webfont.woff') format('woff'),url('/media/fonts/OpenSans-Italic-webfont.ttf') format('truetype');font-weight:normal;font-style:italic}html{color:#333;font-size:14px;line-height:1.5;font-family:'Open Sans',X-LocaleSpecific,sans-serif}body{margin:1.5rem;background:url('/media/img/sandstone/bg-gradient-sky.png') repeat-x,url('/media/img/sandstone/grain.png') repeat,#eee}a{color:#0096dd;text-decoration:none}a:hover,a:focus,a:active{color:#00539f;text-decoration:underline}h1,h2{margin:0;font-family:'Open Sans Light',X-LocaleSpecific-Light,'Open Sans',X-LocaleSpecific,sans-serif;font-weight:normal}main{position:relative;overflow:hidden}header,section,footer{box-sizing:padding-box;margin-top:1.5rem;padding:0 1.5rem}header h1,section h2.iconic{position:relative}header h1:before,section h2.iconic:before{display:block;position:absolute;top:0;background-image:url('/media/img/thunderbird/start/sprite.png');background-repeat:no-repeat;content:''}footer a:before,section a.iconic:before{display:inline-block;-moz-margin-end:.5ex;margin-end:.5ex;width:20px;height:20px;background-image:url('/media/img/thunderbird/start/sprite.png');background-repeat:no-repeat;vertical-align:text-bottom;content:''}header h1{box-sizing:padding-box;font-size:1.25rem;line-height:1}header h1:before{height:100px}header h1 span{display:block;color:#2666a6;font-size:3rem;letter-spacing:-0.1ex}section h2{font-size:1.25rem;line-height:1.3}section h2.iconic{display:table-cell;-moz-padding-start:55px;padding-start:55px;height:50px;vertical-align:middle}section h2:before{width:50px;height:50px}section.tip h2:before{background-position:0 -100px}section.addons h2:before{background-position:-50px -100px}section.help h2:before{background-position:0 -150px}section.blog h2:before{background-position:-50px -150px}section p{margin:.7em 0 0}section a[href$="Contributing"]:before{background-position:-40px -200px}section a.more:after{content:"\00A0\00BB";white-space:nowrap}footer ul{overflow:hidden;margin:0;padding:0;list-style-type:none}footer li{box-sizing:padding-box;padding-bottom:.5rem}footer a[href*="features"]:before{background-position:0 -200px}footer a[href*="blog"]:before{background-position:-20px -200px}footer a[href*="Contributing"]:before{background-position:-40px -200px}footer a[href*="addons"]:before{background-position:-20px -220px}footer a[href*="support"]:before{background-position:-40px -220px}footer a[href*="how"]:before{background-position:0 -220px}[dir="ltr"] header h1:before,[dir="ltr"] section h2.iconic:before{left:0}[dir="rtl"] header h1:before,[dir="rtl"] section h2.iconic:before{right:0}@media(min-width:1024px){footer li{width:33%;min-width:10em}}@media(min-width:800px) and (max-width:1023px){footer li{width:50%}}@media(min-width:800px){main>header,main>div,main>footer{width:50%}[dir="ltr"] main>header,[dir="ltr"] main>div:last-of-type,[dir="ltr"] main>footer,[dir="ltr"] main>footer li{float:left}[dir="ltr"] main>div:first-of-type{float:right}[dir="rtl"] main>header,[dir="rtl"] main>div:last-of-type,[dir="rtl"] main>footer,[dir="rtl"] main>footer li{float:right}[dir="rtl"] main>div:first-of-type{float:left}}@media(min-width:640px) and (max-width:799px){header,section{width:70%}footer{position:absolute;top:120px;width:30%}[dir="ltr"] footer{right:0}[dir="rtl"] footer{left:0}}@media(min-width:480px) and (max-width:639px){footer li{width:33%;min-width:10em}[dir="ltr"] footer li{float:left}[dir="rtl"] footer li{float:right}}@media(min-width:480px){header h1{display:table-cell;-moz-padding-start:110px;padding-start:110px;height:100px;vertical-align:middle}header h1:before{width:100px}}@media(max-width:479px){header h1{padding-top:110px;text-align:center}header h1:before{width:100%;background-position:center top}}

Timestamp: 15-01-01 05:13:15 PM
Warning: Unknown property 'padding-start'.  Declaration dropped.
Source File: [https://mozorg.cdn.mozilla.net/media/css/thunderbird-start-min.css?build=305192a](https://mozorg.cdn.mozilla.net/media/css/thunderbird-start-min.css?build=305192a)
Line: 1, Column: 3127
Source Code:
@font-face{font-family:'Open Sans Light';src:url('/media/fonts/OpenSans-Light-webfont.eot?#iefix') format('embedded-opentype'),url('/media/fonts/OpenSans-Light-webfont.woff') format('woff'),url('/media/fonts/OpenSans-Light-webfont.ttf') format('truetype');font-weight:normal;font-style:normal}@font-face{font-family:'Open Sans Light';src:url('/media/fonts/OpenSans-Semibold-webfont.eot?#iefix') format('embedded-opentype'),url('/media/fonts/OpenSans-Semibold-webfont.woff') format('woff'),url('/media/fonts/OpenSans-Semibold-webfont.ttf') format('truetype');font-weight:bold;font-style:normal}@font-face{font-family:'Open Sans Light';src:url('/media/fonts/OpenSans-LightItalic-webfont.eot?#iefix') format('embedded-opentype'),url('/media/fonts/OpenSans-LightItalic-webfont.woff') format('woff'),url('/media/fonts/OpenSans-LightItalic-webfont.ttf') format('truetype');font-weight:normal;font-style:italic}@font-face{font-family:'Open Sans';src:url('/media/fonts/OpenSans-Regular-webfont.eot?#iefix') format('embedded-opentype'),url('/media/fonts/OpenSans-Regular-webfont.woff') format('woff'),url('/media/fonts/OpenSans-Regular-webfont.ttf') format('truetype');font-weight:normal;font-style:normal}@font-face{font-family:'Open Sans';src:url('/media/fonts/OpenSans-Bold-webfont.eot?#iefix') format('embedded-opentype'),url('/media/fonts/OpenSans-Bold-webfont.woff') format('woff'),url('/media/fonts/OpenSans-Bold-webfont.ttf') format('truetype');font-weight:bold;font-style:normal}@font-face{font-family:'Open Sans';src:url('/media/fonts/OpenSans-Italic-webfont.eot?#iefix') format('embedded-opentype'),url('/media/fonts/OpenSans-Italic-webfont.woff') format('woff'),url('/media/fonts/OpenSans-Italic-webfont.ttf') format('truetype');font-weight:normal;font-style:italic}html{color:#333;font-size:14px;line-height:1.5;font-family:'Open Sans',X-LocaleSpecific,sans-serif}body{margin:1.5rem;background:url('/media/img/sandstone/bg-gradient-sky.png') repeat-x,url('/media/img/sandstone/grain.png') repeat,#eee}a{color:#0096dd;text-decoration:none}a:hover,a:focus,a:active{color:#00539f;text-decoration:underline}h1,h2{margin:0;font-family:'Open Sans Light',X-LocaleSpecific-Light,'Open Sans',X-LocaleSpecific,sans-serif;font-weight:normal}main{position:relative;overflow:hidden}header,section,footer{box-sizing:padding-box;margin-top:1.5rem;padding:0 1.5rem}header h1,section h2.iconic{position:relative}header h1:before,section h2.iconic:before{display:block;position:absolute;top:0;background-image:url('/media/img/thunderbird/start/sprite.png');background-repeat:no-repeat;content:''}footer a:before,section a.iconic:before{display:inline-block;-moz-margin-end:.5ex;margin-end:.5ex;width:20px;height:20px;background-image:url('/media/img/thunderbird/start/sprite.png');background-repeat:no-repeat;vertical-align:text-bottom;content:''}header h1{box-sizing:padding-box;font-size:1.25rem;line-height:1}header h1:before{height:100px}header h1 span{display:block;color:#2666a6;font-size:3rem;letter-spacing:-0.1ex}section h2{font-size:1.25rem;line-height:1.3}section h2.iconic{display:table-cell;-moz-padding-start:55px;padding-start:55px;height:50px;vertical-align:middle}section h2:before{width:50px;height:50px}section.tip h2:before{background-position:0 -100px}section.addons h2:before{background-position:-50px -100px}section.help h2:before{background-position:0 -150px}section.blog h2:before{background-position:-50px -150px}section p{margin:.7em 0 0}section a[href$="Contributing"]:before{background-position:-40px -200px}section a.more:after{content:"\00A0\00BB";white-space:nowrap}footer ul{overflow:hidden;margin:0;padding:0;list-style-type:none}footer li{box-sizing:padding-box;padding-bottom:.5rem}footer a[href*="features"]:before{background-position:0 -200px}footer a[href*="blog"]:before{background-position:-20px -200px}footer a[href*="Contributing"]:before{background-position:-40px -200px}footer a[href*="addons"]:before{background-position:-20px -220px}footer a[href*="support"]:before{background-position:-40px -220px}footer a[href*="how"]:before{background-position:0 -220px}[dir="ltr"] header h1:before,[dir="ltr"] section h2.iconic:before{left:0}[dir="rtl"] header h1:before,[dir="rtl"] section h2.iconic:before{right:0}@media(min-width:1024px){footer li{width:33%;min-width:10em}}@media(min-width:800px) and (max-width:1023px){footer li{width:50%}}@media(min-width:800px){main>header,main>div,main>footer{width:50%}[dir="ltr"] main>header,[dir="ltr"] main>div:last-of-type,[dir="ltr"] main>footer,[dir="ltr"] main>footer li{float:left}[dir="ltr"] main>div:first-of-type{float:right}[dir="rtl"] main>header,[dir="rtl"] main>div:last-of-type,[dir="rtl"] main>footer,[dir="rtl"] main>footer li{float:right}[dir="rtl"] main>div:first-of-type{float:left}}@media(min-width:640px) and (max-width:799px){header,section{width:70%}footer{position:absolute;top:120px;width:30%}[dir="ltr"] footer{right:0}[dir="rtl"] footer{left:0}}@media(min-width:480px) and (max-width:639px){footer li{width:33%;min-width:10em}[dir="ltr"] footer li{float:left}[dir="rtl"] footer li{float:right}}@media(min-width:480px){header h1{display:table-cell;-moz-padding-start:110px;padding-start:110px;height:100px;vertical-align:middle}header h1:before{width:100px}}@media(max-width:479px){header h1{padding-top:110px;text-align:center}header h1:before{width:100%;background-position:center top}}

Timestamp: 15-01-01 05:13:15 PM
Warning: Unknown property 'padding-start'.  Declaration dropped.
Source File: [https://mozorg.cdn.mozilla.net/media/css/thunderbird-start-min.css?build=305192a](https://mozorg.cdn.mozilla.net/media/css/thunderbird-start-min.css?build=305192a)
Line: 1, Column: 5178
Source Code:
@font-face{font-family:'Open Sans Light';src:url('/media/fonts/OpenSans-Light-webfont.eot?#iefix') format('embedded-opentype'),url('/media/fonts/OpenSans-Light-webfont.woff') format('woff'),url('/media/fonts/OpenSans-Light-webfont.ttf') format('truetype');font-weight:normal;font-style:normal}@font-face{font-family:'Open Sans Light';src:url('/media/fonts/OpenSans-Semibold-webfont.eot?#iefix') format('embedded-opentype'),url('/media/fonts/OpenSans-Semibold-webfont.woff') format('woff'),url('/media/fonts/OpenSans-Semibold-webfont.ttf') format('truetype');font-weight:bold;font-style:normal}@font-face{font-family:'Open Sans Light';src:url('/media/fonts/OpenSans-LightItalic-webfont.eot?#iefix') format('embedded-opentype'),url('/media/fonts/OpenSans-LightItalic-webfont.woff') format('woff'),url('/media/fonts/OpenSans-LightItalic-webfont.ttf') format('truetype');font-weight:normal;font-style:italic}@font-face{font-family:'Open Sans';src:url('/media/fonts/OpenSans-Regular-webfont.eot?#iefix') format('embedded-opentype'),url('/media/fonts/OpenSans-Regular-webfont.woff') format('woff'),url('/media/fonts/OpenSans-Regular-webfont.ttf') format('truetype');font-weight:normal;font-style:normal}@font-face{font-family:'Open Sans';src:url('/media/fonts/OpenSans-Bold-webfont.eot?#iefix') format('embedded-opentype'),url('/media/fonts/OpenSans-Bold-webfont.woff') format('woff'),url('/media/fonts/OpenSans-Bold-webfont.ttf') format('truetype');font-weight:bold;font-style:normal}@font-face{font-family:'Open Sans';src:url('/media/fonts/OpenSans-Italic-webfont.eot?#iefix') format('embedded-opentype'),url('/media/fonts/OpenSans-Italic-webfont.woff') format('woff'),url('/media/fonts/OpenSans-Italic-webfont.ttf') format('truetype');font-weight:normal;font-style:italic}html{color:#333;font-size:14px;line-height:1.5;font-family:'Open Sans',X-LocaleSpecific,sans-serif}body{margin:1.5rem;background:url('/media/img/sandstone/bg-gradient-sky.png') repeat-x,url('/media/img/sandstone/grain.png') repeat,#eee}a{color:#0096dd;text-decoration:none}a:hover,a:focus,a:active{color:#00539f;text-decoration:underline}h1,h2{margin:0;font-family:'Open Sans Light',X-LocaleSpecific-Light,'Open Sans',X-LocaleSpecific,sans-serif;font-weight:normal}main{position:relative;overflow:hidden}header,section,footer{box-sizing:padding-box;margin-top:1.5rem;padding:0 1.5rem}header h1,section h2.iconic{position:relative}header h1:before,section h2.iconic:before{display:block;position:absolute;top:0;background-image:url('/media/img/thunderbird/start/sprite.png');background-repeat:no-repeat;content:''}footer a:before,section a.iconic:before{display:inline-block;-moz-margin-end:.5ex;margin-end:.5ex;width:20px;height:20px;background-image:url('/media/img/thunderbird/start/sprite.png');background-repeat:no-repeat;vertical-align:text-bottom;content:''}header h1{box-sizing:padding-box;font-size:1.25rem;line-height:1}header h1:before{height:100px}header h1 span{display:block;color:#2666a6;font-size:3rem;letter-spacing:-0.1ex}section h2{font-size:1.25rem;line-height:1.3}section h2.iconic{display:table-cell;-moz-padding-start:55px;padding-start:55px;height:50px;vertical-align:middle}section h2:before{width:50px;height:50px}section.tip h2:before{background-position:0 -100px}section.addons h2:before{background-position:-50px -100px}section.help h2:before{background-position:0 -150px}section.blog h2:before{background-position:-50px -150px}section p{margin:.7em 0 0}section a[href$="Contributing"]:before{background-position:-40px -200px}section a.more:after{content:"\00A0\00BB";white-space:nowrap}footer ul{overflow:hidden;margin:0;padding:0;list-style-type:none}footer li{box-sizingadding-box;padding-bottom:.5rem}footer a[href*="features"]:before{background-position:0 -200px}footer a[href*="blog"]:before{background-position:-20px -200px}footer a[href*="Contributing"]:before{background-position:-40px -200px}footer a[href*="addons"]:before{background-position:-20px -220px}footer a[href*="support"]:before{background-position:-40px -220px}footer a[href*="how"]:before{background-position:0 -220px}[dir="ltr"] header h1:before,[dir="ltr"] section h2.iconic:before{left:0}[dir="rtl"] header h1:before,[dir="rtl"] section h2.iconic:before{right:0}@media(min-width:1024px){footer li{width:33%;min-width:10em}}@media(min-width:800px) and (max-width:1023px){footer li{width:50%}}@media(min-width:800px){main>header,main>div,main>footer{width:50%}[dir="ltr"] main>header,[dir="ltr"] main>div:last-of-type,[dir="ltr"] main>footer,[dir="ltr"] main>footer li{float:left}[dir="ltr"] main>div:first-of-type{float:right}[dir="rtl"] main>header,[dir="rtl"] main>div:last-of-type,[dir="rtl"] main>footer,[dir="rtl"] main>footer li{float:right}[dir="rtl"] main>div:first-of-type{float:left}}@media(min-width:640px) and (max-width:799px){header,section{width:70%}footer{position:absolute;top:120px;width:30%}[dir="ltr"] footer{right:0}[dir="rtl"] footer{left:0}}@media(min-width:480px) and (max-width:639px){footer li{width:33%;min-width:10em}[dir="ltr"] footer li{float:left}[dir="rtl"] footer li{float:right}}@media(min-width:480px){header h1{display:table-cell;-moz-padding-start:110px;padding-start:110px;height:100px;vertical-align:middle}header h1:before{width:100px}}@media(max-width:479px){header h1{padding-top:110px;text-align:center}header h1:before{width:100%;background-position:center top}} 
```

And that's just Thunderbird on a fresh install.

In Firefox, the search window has been changed; it no longer drops down with a choice of engines.

Are these not things that Canonical changed?

Thanks.

---

### Post by vasa1 on 2015-01-01
> **KitchM said:**
> 
... In Firefox, the search window has been changed; it no longer drops down with a choice of engines.

Are these not things that Canonical changed?
...
AFAIK, no.

---

### Post by Frogs Hair on 2015-01-01
I think the change in the search box menu happened in the Firefox version when Mozilla changed to Yahoo as the default search engine. I notice the menu is automated when a search term is entered and this change is not a Ubuntu modification.

---

### Post by whitesmith on 2015-01-02
There's no connection between Canonical and Mozilla. Try Chromium if you don't like Firefox. Regards.

---

### Post by buzzingrobot on 2015-01-02
What Thunderbird version?  I don't see those errors here on 31.3.0, which I believe is the current version from the repos.

 Failures to read a file can often be traced to incorrect file permissions, as well as simple nonexistence of the file. My system here has no "/usr/lib/thunderbird/extensions...." folder.  But it does have a "~/.mozilla/extensions" folder.  Did you, perhaps, run Thunderbird as root and install some extensions?

If you do have extensions/plugins enabled in Thunderbird, disable all of them and restart.  If the error does not appear, enable each, one at a time, restarting each time, and see if one of the extensions/plugins triggers the error.

Do all files tagged 'junk' trigger the error, or just files from a specific sender?

Check for a search panel in Preferences. (I'm on Unity at the moment and it's there and allows multiple search engine options to be enabled.)

Canonical does add a a few extensions to Firefox and Thunderbird on Unity to provide better integration with that interface.

---

### Post by Dennis N on 2015-01-02
> How can one get the plain, stock versions? 

You can download the "original" Linux version from:

[https://www.mozilla.org/](https://www.mozilla.org/)

It will work fine in Xubuntu, and offer to update itself with new versions. It will not appear automatically into your menu. You will have to set it up yourself, so it requires knowledge of how to do that. Check their website for guides.

---

### Post by Yellow Pasque on 2015-01-02
> **Frogs Hair said:**
> I think the change in the search box menu happened in the Firefox version when Mozilla changed to Yahoo as the default search engine

Yeah, it changed in FF 34. If you want the old search menu behavior, enter "about:config" in the URL bar and toggle the "browser.search.showOneOffButtons" key.

---

### Post by monkeybrain20122 on 2015-01-03
For forefox you can undo all Canonoical modifications by going to Tools > addons > extensions and disable all etntries related to Ubuntu. However I don't think your problems have anything to do with those, and I still have the dropdown for search engines. It maybe something in your settings, start with a fresh profile and see if you still experience those odd behaviours (Close FF, open file manager to your home, press ctrl + h or choose 'show hidden' from menu then rename the hidden folder .mozilla to .mozilla-bak, then start FF and a new profile and new .mozilla will be created. To return to the old profile, close FF, delete .mozilla and then rename .mozilla-bak back to .mozilla and start FF)

Sorry, don't use an email client so can't help with thunderbird.

---

### Post by vasa1 on 2015-01-03
> **Temüjin said:**
> Yeah, it changed in FF 34. If you want the old search menu behavior, enter "about:config" in the URL bar and toggle the "browser.search.showOneOffButtons" key.

+1.

[http://forums.mozillazine.org/viewtopic.php?f=38&t=2895275](http://forums.mozillazine.org/viewtopic.php?f=38&t=2895275)
[http://forums.mozillazine.org/viewtopic.php?f=7&t=2890187](http://forums.mozillazine.org/viewtopic.php?f=7&t=2890187)

I don't use the search bar at all and have removed it from my UI. Searching from the address bar is good enough for me.

---

