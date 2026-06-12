---
title: "PTFB Equivalent? (Push The Freakin Button)"
date: 2017-01-12
forum: General Help
---

### Post by Robert_Gaines on 2017-01-12
There was a software that I used back in the days of Windows Me that is apparently still an on going project that I once used to close dialogue windows called PTFB (Push The Freakin Button). I there an equivalent software for Ubuntu?

---

### Post by TheFu on 2017-01-12
Not sure - xkill?

---

### Post by Robert_Gaines on 2017-01-12
I suppose that would terminate an application, but PTFB actively checks dialog windows for certain information to identify it. If I have listed that dialog box as one I wish to be automatically closed, it will perform a virtual mouse click over the button I wish it to click on. It's kind of more like a temporary solution to an updating issue I've been having that does not seem to have a working solution. I get a dialog box informing me that data files can't be downloaded for ttf-msfonts-installer. No solutions work. Although, I probably should just uninstall the stupid thing because it is probably no longer supported and the fonts aren't working.

---

### Post by TheFu on 2017-01-12
$ xdotool search --name [name of the window] key [keys to press]

[http://xmodulo.com/simulate-key-press-mouse-movement-linux.html](http://xmodulo.com/simulate-key-press-mouse-movement-linux.html) has more.

I use xdotool for all sorts of things. Mainly to provide accel keyboard shortcuts for launching programs I like.

---

### Post by ian-weisser on 2017-01-12
Ubuntu developers work very hard to ensure that you are not spammed by uneccessary dialog boxes.
There are a [set of guidelines]("https://wiki.ubuntu.com/NotificationDevelopmentGuidelines") for which kinds of important events should be dialogs, and which lesser events should non-interactive notifications.

If you feel that an Ubuntu application or service is not following those guidelines properly, or spamming you with irrelevant dialog boxes, then please file a bug report against that application.
It is certainly possible to close, kill, or even properly respond to dialog boxes via several x and dbus mechanisms in addition to the suggestions already made. However, they get a bit complicated.

In your case of a failed ttf-msfonts-installer package install, it would be better if you finally just took a moment to either install or uninstall the package. Either would solve the problem once and for all.

---

### Post by Robert_Gaines on 2017-01-12
I agree that just uninstalling ttf-msfronts-installer would be the best solution, but it sure is boring to go that route. Well, I mean, scripting is fun, but there really isn't much use for it any more. I remember when it was fun to create your own web site of raw HTML code and Javascript. I stopped doing that because my ISP disabled web hosting with their free ftp, Yahoo Geocities was discontinued, and free hosting sites block javascript, CSS,  and certain HTML page formatting. It seems like coding is being dropped for wizards and special editors, but the fundamental sentiment of coding things for yourself is dead. I have repeatedly uninstalled and/or reinstalled tts-msfonts-installer without getting any use from it. I will go ahead and uninstall the package for now, and check in the future for any fixes in it if I still wish to have it.

The xdotool scripting does interest me so may be I might find some use for it in the future.

---

### Post by Olav on 2017-01-13
The name of the package is [ttf-mscorefonts-installer](http://packages.ubuntu.com/search?keywords=ttf-mscorefonts-installer), not ttf-msfonts-installer. There is a bug in that package, it tries to download the fonts from the wrong (outdated) location. I believe this is already known and being fixed. What solved it for me was to install the (more recent) [package](https://packages.debian.org/search?keywords=ttf-mscorefonts-installer) from Debian Jessie.

---

### Post by howefield on 2017-01-13
> **Robert_Gaines said:**
> ... I get a dialog box informing me that data files can't be downloaded for ttf-msfonts-installer. No solutions work. Although, I probably should just uninstall the stupid thing because it is probably no longer supported and the fonts aren't working.

This thread might be of interest : [https://ubuntuforums.org/showthread.php?t=1696082](https://ubuntuforums.org/showthread.php?t=1696082). There are a couple of possible pointers including the xdotools mentioned above.

In the specific case of ttf-mecorefonts-installer sourceforge (where the actual font files are downloaded from) changed the location that the fonts are stored rendering the package broken. Boring or not, I'd suggest purging that broken 3.4 version of the package and instead install the 3.6 version of the package from an alternative source, eg

```
sudo apt purge ttf-mscorefonts-installer
```

to get rid of the current package

```
wget http://ftp.de.debian.org/debian/pool/contrib/m/msttcorefonts/ttf-mscorefonts-installer_3.6_all.deb -P ~/Downloads
```

to download the 3.6 version of the package to your Downloads folder, and

```
sudo apt install ~/Downloads/ttf-mscorefonts-installer_3.6_all.deb
```

to install the new package.

---

