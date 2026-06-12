---
title: "can't load Vimeo videos"
date: 2015-03-30
forum: General Help
---

### Post by jlh68 on 2015-03-30
I can not load (play) Vimeo videos.  The Vimeo site seems the think that some gstreamer stuff is needed.  I checked my system and I know have two out of the thre and I could not download the third.

I am using Ubuntu 14.04 LTS with Firefox 36.04 with Flash plugin.

In searching the WEB, it looks like Vimeo also may not work  on a Windows OS, on a Mac OS as well as  Linux.  I found a lot of posts by many people that are having trouble with Vimeo.  Is Vimeo half baked?

---

### Post by Vladlenin5000 on 2015-03-30
Vimeo works fine on mine and always worked. 
It no longer requires Flash, but HTML5.

---

### Post by jlh68 on 2015-03-30
It does not work on my system even with HTML5.

---

### Post by mc4man on 2015-03-30
how about - 
```
sudo apt-get install gstreamer1.0-libav
```

---

### Post by jlh68 on 2015-03-31
Most recent version was already installed.  I think that is one of the two of three the Vimeo F&Q site said was needed.

>  Why can’t I play videos on Linux / Ubuntu?
In order to play Vimeo videos on Ubuntu (and some other Linux operating systems), you will need the following packages:

Chromium: 
chromium-codecs-ffmpeg-extra

Firefox: 
gstreamer0.10-plugins-good 
streamer0.10-ffmpeg

The one I can't get is the last one:  *streamer0.10-ffmpeg* In fact the latest is streamer0.10-04-ffmpeg.  Still can not get it.

---

### Post by Frogs Hair on 2015-03-31
Works fine here also with the Ubuntu-restriced-extras. Are you using any browser extensions that might interfere/block with play back ?

---

### Post by mc4man on 2015-03-31
> **jlh68 said:**
> Most recent version was already installed.  I think that is one of the two of three the Vimeo F&Q site said was needed.



The one I can't get is the last one:  *streamer0.10-ffmpeg* In fact the latest is streamer0.10-04-ffmpeg.  Still can not get it.
With any recent firefox gstreamer0.10-ffmpeg is not needed, gstreamer[COLOR="#0000CD"]1.0[/COLOR]-libav is what should be used.
If you want to try gstreamer0.10-ffmpeg then I have here as it's no longer produced in Debian/Ubuntu
[https://launchpad.net/~mc3man/+archive/ubuntu/gstffmpeg-keep](https://launchpad.net/~mc3man/+archive/ubuntu/gstffmpeg-keep)

---

### Post by grahammechanical on 2015-03-31
Is this of interest?

[http://www.omgubuntu.co.uk/2015/03/firefox-37-download-new-features](http://www.omgubuntu.co.uk/2015/03/firefox-37-download-new-features)

---

### Post by jlh68 on 2015-04-01
OK guys, I made two changes, first I upgraded Firefox to ver 37 which is supposed to help in this.  It did not work.  Why?  Well because  i had Flashblock "on". I thought Flashblock would let one click the Flash symbol and then Flash would load.  Obviously Flashblock works with some flash files and not with others, well  I mean it will block them even though it is supposed to allow flash files when the Icon is clicked.

Bottom line is I do not know if Vimeo would have worked with FF 36.04 and Flashblock "off".  I do know Vimeo loaded with FF37 and Flashblock "off".

lI think the developer of Flashblock has some work to do on the add-on to make it compatible with ALL Flash/Video files.

Thanks for all the suggestions.

Firefox ver-37 was released this morning (2015.04.01).

---

### Post by Holger_Gehrke on 2015-04-01
> **jlh68 said:**
> ... I thought Flashblock would let one click the Flash symbol and then Flash would load.  Obviously Flashblock works with some flash files and not with others, well  I mean it will block them even though it is supposed to allow flash files when the Icon is clicked. ...


It's a bit more complicated than this. Some sites offer both html and flash through the same page and have a javascript which selects which to show by basically putting one on top of the other and / or hiding one or the other. Flashblock and these scripts are quite often interfering with each other, which can lead to a situation where the site's script puts the html5 video in front but for some reason can't start it playing and flashblock can't get your click because the (broken and invisible) html5 video gets your clicks ... In such situations you have two options: disable flash completely or disable flashblock; either one can work but it's kind of hard to tell which works on which site.

---

### Post by monkeybrain20122 on 2015-04-01
> **Holger_Gehrke said:**
> It's a bit more complicated than this. Some sites offer both html and flash through the same page and have a javascript which selects which to show by basically putting one on top of the other and / or hiding one or the other. Flashblock and these scripts are quite often interfering with each other, which can lead to a situation where the site's script puts the html5 video in front but for some reason can't start it playing and flashblock can't get your click because the (broken and invisible) html5 video gets your clicks ... In such situations you have two options: disable flash completely or disable flashblock; either one can work but it's kind of hard to tell which works on which site.

There is no need for flashblock anymore. Now the function is built into Firefox (has been since FF 2x) Just go to Tools > Addons and remove flashblock and then go to plugins and set flash to "Ask to Activate", then flash won't load automatically without permission.

---

### Post by Holger_Gehrke on 2015-04-02
> **monkeybrain20122 said:**
> There is no need for flashblock anymore. Now the function is built into Firefox (has been since FF 2x) Just go to Tools > Addons and remove flashblock and then go to plugins and set flash to "Ask to Activate", then flash won't load automatically without permission.

This activates or deactivates all flash-elements on the whole page. If you want to selectively activate one flash-element on a page full of them, flashblock still makes sense ...

---

