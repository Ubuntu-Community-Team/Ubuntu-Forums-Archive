---
title: "Installing Adobe Flash and other stuff"
date: 2013-09-18
forum: General Help
---

### Post by Fedoraguy on 2013-09-18
[FONT=arial, sans-serif]I have recently installed Ubuntu 12.04 LTS on my Samsung Chromebook 303c, and I found that Linux does not have Adobe Flash, so how do I install Adobe Flash, on Ubuntu, on my Chromebook?  Also what code do I use to switch from Ubuntu back to Chrome OS, instead of resetting developer mode? Could anyone please help me?  All the other sources I used were for different models, Please HELP!  I have been able to install Chromium on Ubuntu which is [/FONT]*supposed *[FONT=arial, sans-serif]to come with pepper flash, but that doesn't work, also how do I install Google Earth Plugin for my web browser? Seeing the folks at Google didn't stop to think about having all of their official google apps compatible for Chrome OS in the first place.[/FONT]

---

### Post by slickymaster on 2013-09-18
Here's how you can add Adobe Flash to your Ubuntu:

1. Open the Ubuntu Software Center.
2. Type "flash" without quotes into the search box and hit enter.
3. Click on Adobe Flash Plugin in the search results.
4. Click the Install button.

To install Google Earth see this: [Google Earth - Recommended installation methods]("https://help.ubuntu.com/community/GoogleEarth#Recommended_installation_methods")

---

### Post by deadflowr on 2013-09-18
Google-Chrome and Chromium are different browsers.
Google-Chrome(which is not available in the Ubuntu software center) comes with pepperflash.
Chromium(which is available in the Ubuntu software center) does not come with pepperflash.

---

### Post by Fedoraguy on 2013-09-18
> **slickymaster said:**
> Here's how you can add Adobe Flash to your Ubuntu:

1. Open the Ubuntu Software Center.
2. Type "flash" without quotes into the search box and hit enter.
3. Click on Adobe Flash Plugin in the search results.
4. Click the Install button.

To install Google Earth see this: [Google Earth - Recommended installation methods]("https://help.ubuntu.com/community/GoogleEarth#Recommended_installation_methods")

Flash was not listed in the software center, I checked, even when I installed in manually from Adobe it had of course opened up Ubuntu Software Center and it Still wasn't there!  So whats the deal, also the Google Earth thing, tried that too. Didn't work.

---

### Post by deadflowr on 2013-09-18
Can you find the program "flashplugin-installer'?

---

### Post by slickymaster on 2013-09-18
> **deadflowr said:**
> Can you find the program "flashplugin-installer'?

deadflowr is right. Type "flashplugin-installer" instead, in the search box.

> **Fedoraguy said:**
> ...So whats the deal, also the Google Earth thing, tried that too. Didn't work.

Can you be more specific? What didn't work?

---

### Post by bibek2 on 2013-09-18
how about ubuntu-restricted-extras ? does that have flash ?

---

### Post by slickymaster on 2013-09-18
> **bibek2 said:**
> how about ubuntu-restricted-extras ? does that have flash ?

Yes. Ubuntu Restricted Extras is a “meta-package”, which installs a number of other packages you could find separately in the Software Center if you wanted to. These packages, by name, are:
[LIST]
[*]flashplugin-installer
[*]gstreamer0.10-ffmpeg
[*]gstreamer0.10-fluendo-mp3
[*]gstreamer0.10-pitfdll
[*]gstreamer0.10-plugins-bad
[*]gstreamer0.10-plugins-ugly
[*]gstreamer0.10-plugins-bad-multiverse
[*]gstreamer0.10-plugins-ugly-multiverse
[*]icedtea6-plugin
[*]libavcodec-extra-52
[*]libmp4v2-0
[*]ttf-mscorefonts-installer
[*]unrar
[/LIST]

---

### Post by grahammechanical on 2013-09-18
Pepper Flash is installed through a PPA.

[http://www.webupd8.org/2013/04/install-pepper-flash-player-for.html](http://www.webupd8.org/2013/04/install-pepper-flash-player-for.html)

---

