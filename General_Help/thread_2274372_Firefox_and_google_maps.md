---
title: "Firefox and google maps"
date: 2015-04-19
forum: General Help
---

### Post by brian61 on 2015-04-19
Help!

New to linux, running a dual boot on my new asus zenbook and really enjoying ubuntu so far. The only issue I have hit is that firefox and google maps DO NOT get along. Things go black, fonts go crazy, and I have to force close the browser. 

It runs fine in chrome.

I have found a few articles online suggesting 2 things:

1) enable WebGL
2) Disable hardware acceleration.

Neither has had any effect.

Ideas? besides use chrome :p

-brian

---

### Post by monkeybrain20122 on 2015-04-19
Works here. I have only manually enabled layers.acceleration.forced-enabled and layers.offmainthreadcomosition.enabled from about:config and nothing else. Several years old second hand Dell laptop, graphic card is intel ironlake, hardly top of the line.

---

### Post by Holger_Gehrke on 2015-04-20
You could try to switch to the "classic" google maps, this is slightly better in terms of compatibility. Click on the "?" (somewhere on the lower right) and select it from the menu that pops up. This workaround will sadly stop working sometime soon since google has already said they are going to retire the classic mode.

---

### Post by Bucky Ball on 2015-04-20
Have you installed third-party plug-ins, etc.? You may need Java to use Google maps. You can install openjdk-7-jre (on 14.**, not sure of the version in releases prior to) from Software Centre (the official repositories). That might drag in icedtea-7-plugin, which is what you want for Firefox to run Java pages, but if it doesn't, install that, too.

You can also install ubuntu-restricted-extras which should drag in Java, but also a heap of other stuff you may/may not want/need.

---

### Post by Holger_Gehrke on 2015-04-20
Sorry to contradict you, Bucky Ball, but Google Maps does not use Java. Tons of JavaScript and a bit of flash (for streetview) but no java. No '<applet>' tags or '<object>' with the kind of attributes you'd need for running a java program anywhere in the page source.

---

### Post by Bucky Ball on 2015-04-20
> **Holger_Gehrke said:**
> Sorry to contradict you, Bucky Ball, but Google Maps does not use Java. 

No problems, as you haven't. I said Google maps 'may' need Java. I had no idea either way, but you have cleared up the fact it doesn't. Thanks. ;)

I have openjdk-7-jre and icedtea installed and Google Maps is faultless for me. Obviously it is not because of openjdk or icedtea.

---

### Post by monkeybrain20122 on 2015-04-20
> **Holger_Gehrke said:**
> You could try to switch to the "classic" google maps, this is slightly better in terms of compatibility. Click on the "?" (somewhere on the lower right) and select it from the menu that pops up. This workaround will sadly stop working sometime soon since google has already said they are going to retire the classic mode.

"classoc map" is deprecated, now you will be sent to light mode if your machine doesn't support 3d map. Not sure what happen if it supports 3d map but you prefer lite mode. 
[http://ubuntuforums.org/showthread.php?t=2273904&p=13266070#post13266070](http://ubuntuforums.org/showthread.php?t=2273904&p=13266070#post13266070)

---

### Post by brian61 on 2015-04-20
Thanks all, Ill give some of your suggestions a try when I get home from work.

Odd that things would work in Chrome but not Firefox.

/shrug

---

### Post by tripp98 on 2015-04-20
+1 to bucky.  sudo apt-get install ubuntu-restricted-extras

its flash.  Chrome has a flash like thing installed.  the restricted extras will get flash for firefox.

---

### Post by Holger_Gehrke on 2015-04-20
> **monkeybrain20122 said:**
> "classoc map" is deprecated, now you will be sent to light mode if your machine doesn't support 3d map.

It seems that the ... "upgrade" ... is done at different times depending on geography. Right now in Germany I can still get the old google maps, which is good since I could never get streetview working with the new maps. Somebody on slashdot suggested that the parameter "output=classic" appended to the url like so: "https://maps.google.com/maps?output=classic " might keep on working even if the option in the menu is gone ...

---

### Post by brian61 on 2015-04-20
Installed the restricted extras with sudo apt-get install ubuntu-restricted-extras

Still nothing, firefox shows the flash plugin is up to date and installed.

Its not a hardware issue (I assume) since it works in other browsers (chrome).

Thoughts?

Navigating to [https://maps.google.com/maps?output=classic](https://maps.google.com/maps?output=classic) works fine, including street view, but id like to not have to use the old version which will be gone soon.

---

### Post by Holger_Gehrke on 2015-04-20
It might be that firefox tries to run the full (webgl) version of the new maps and fails. Try forcing the lite-mode by using "output=lite".

---

### Post by monkeybrain20122 on 2015-04-20
What is your graphic card?

---

### Post by brian61 on 2015-04-20
> **monkeybrain20122 said:**
> What is your graphic card?

Its an asus zenbook with "Integrated Intel® HD Graphics 5300"

full specs here:

[http://www.asus.com/us/Notebooks_Ultrabooks/ASUS_ZENBOOK_UX305FA/specifications/](http://www.asus.com/us/Notebooks_Ultrabooks/ASUS_ZENBOOK_UX305FA/specifications/)

---

### Post by brian61 on 2015-04-20
> **Holger_Gehrke said:**
> It might be that firefox tries to run the full (webgl) version of the new maps and fails. Try forcing the lite-mode by using "output=lite".

lite mode and classic mode run just fine, everything works properly in chrome.

---

### Post by brian61 on 2015-04-20
Thank you all for helping work through this by the way. This is what I have come to expect from the Linux community.

-brian

---

### Post by monkeybrain20122 on 2015-04-20
Just to be clear, what do you mean by not work?

---

### Post by brian61 on 2015-04-20
> **monkeybrain20122 said:**
> Just to be clear, what do you mean by not work?


I have attached a screenshot.[ATTACH=CONFIG]261444[/ATTACH]

---

### Post by monkeybrain20122 on 2015-04-20
Not sure why. I tested on Fedora 21 on the same machine, different partition and 3d map sort of works on Firefox there but very slow (but Chrome is fast). But here on Ubuntu it works perfectly on Both Firefox and Chrome. I was thinking that maybe I have more up to date driver on Ubuntu installed via [https://launchpad.net/~oibaf/+archive/ubuntu/graphics-drivers](https://launchpad.net/~oibaf/+archive/ubuntu/graphics-drivers) But then I didn't see a blackscreen like you even on Fedora.

---

### Post by brian61 on 2015-04-20
I downloaded a piece of software called system profiler. It says my openGL renderer is "unknown"? Am I missing drivers? I'm not sure how all that works on linux.

from my specs:

> -Computer-
Processor        : 4x Intel(R) Core(TM) M-5Y10c CPU @ 0.80GHz
Memory        : 8077MB (946MB used)
Operating System        : Ubuntu 14.04.2 LTS
User Name        : brian (Brian)
Date/Time        : Mon 20 Apr 2015 07:53:30 PM MDT
-Display-
Resolution        : 1920x1080 pixels
OpenGL Renderer        : Unknown
X11 Vendor        : The X.Org Foundation
-Multimedia-
Audio Adapter        : HDA-Intel - HDA Intel HDMI
Audio Adapter        : HDA-Intel - HDA Intel PCH
-Input Devices-
 Lid Switch
 Sleep Button
 Power Button
 AT Translated Set 2 keyboard
 ETPS/2 Elantech Touchpad
 HDA Intel PCH Mic
 HDA Intel PCH Headphone
 USB2.0 UVC HD Webcam
 Video Bus
 Asus WMI hotkeys
 HDA Intel HDMI HDMI/DP,pcm        : 3=
 HDA Intel HDMI HDMI/DP,pcm        : 7=
 HDA Intel HDMI HDMI/DP,pcm        : 8=
-Printers-
No printers found
-SCSI Disks-
ATA Micron_M600_MTFD



Also, maps runs fine in firefox on my windows 8.1 partition for what thats worth.

---

### Post by monkeybrain20122 on 2015-04-20
```
$ glxinfo | grep OpenGL
OpenGL vendor string: Intel Open Source Technology Center
OpenGL renderer string: Mesa DRI Intel(R) Ironlake Mobile 
OpenGL version string: 2.1 Mesa 10.6.0-devel (git-1eac3ae 2015-04-18 trusty-oibaf-ppa)
OpenGL shading language version string: 1.20
OpenGL extensions:
OpenGL ES profile version string: OpenGL ES 2.0 Mesa 10.6.0-devel (git-1eac3ae 2015-04-18 trusty-oibaf-ppa)
OpenGL ES profile shading language version string: OpenGL ES GLSL ES 1.0.16
OpenGL ES profile extension
```

Here is mine. Like I said hardly cutting edge. 

To see this output download mesa-utils from the Software Centre and run 

```
glxinfo | grep OpenGL
```

---

### Post by brian61 on 2015-04-20
What I get.

> 

OpenGL vendor string: Intel Open Source Technology Center
OpenGL renderer string: Mesa DRI Intel(R) HD Graphics 5300 (Broadwell GT2) 
OpenGL core profile version string: 3.3 (Core Profile) Mesa 10.3.2
OpenGL core profile shading language version string: 3.30
OpenGL core profile context flags: (none)
OpenGL core profile profile mask: core profile
OpenGL core profile extensions:
OpenGL version string: 3.0 Mesa 10.3.2
OpenGL shading language version string: 1.30
OpenGL context flags: (none)
OpenGL extensions:



---

### Post by monkeybrain20122 on 2015-04-20
No idea. You have have a better card than mine. Possibly mesa 10.3 is too old? Did you set about:config like I said in my first post?

---

### Post by brian61 on 2015-04-20
Yep, no change. I have tried safe mode, as well, nada. :-({|=

Very frustrating, this is literally the only issue I have had with Linux, everything else has been a great experience thus far.

Ill be sticking with Chrome for the time being I guess.

---

### Post by monkeybrain20122 on 2015-04-20
Maybe you shouldn't have disabled hardware acceleration. 

You can also try upgrading your driver from the ppa I posted above. But there is always some risk in using beta driver, so if you want to try that have ppa-purge ready in case something goes wrong.

---

### Post by brian61 on 2015-05-06
Just a heads up, updating to 15.04 seems to have fixed whatever was causing this issue.

Cheers,

-brian

---

