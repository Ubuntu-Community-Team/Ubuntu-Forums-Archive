---
title: "Flash and Shockwave Installation"
date: 2007-01-16
forum: General Help
---

### Post by dothedorky on 2007-01-16
I've been torturing myself with my current flashplayer (or lack there of). I'm positive i have flash 7 installed (without a previous version of flash, i'm sure i wouldnt be able to see most things). Youtube works, but various miscellaneous videos on various sites ([www.mtv.com/overdrive](www.mtv.com/overdrive), for example)

Let me just say, i've tried EVERYTHING to get flash player 9 to work. I've been through COUNTLESS walkthroughs, and also tried following the instructions from adobe when i tried to download it. Nothing seems to be working. 

I am also trying to download shockwave player, to possibly play games on shockwave.com.

When i type in my browser "about : plugins" it says the following:

```

[B]Shockwave Flash

    File name: libflashplayer.so
    Shockwave Flash 7.0 r68
[/B]
MIME Type 	                     Description 	         Suffixes  Enabled
application/x-shockwave-flash 	Shockwave Flash 	swf 	Yes
application/futuresplash 	FutureSplash Player 	   spl 	    Yes
[B]
Java(TM) Plug-in 1.5.0_06-b05

    File name: libjavaplugin_oji.so
    Java(TM) Plug-in 1.5.0_06[/B]

application/x-java-vm 	                       Java 		               Yes
application/x-java-applet 	              Java 		               Yes
application/x-java-applet;version=1.1 	 Java 		                Yes
application/x-java-applet;version=1.1.1 Java 		               Yes
application/x-java-applet;version=1.1.2 	Java 		Yes
application/x-java-applet;version=1.1.3 	Java 		Yes
application/x-java-applet;version=1.2 	Java 		                Yes
application/x-java-applet;version=1.2.1 	Java 		Yes
application/x-java-applet;version=1.2.2 	Java 		Yes
application/x-java-applet;version=1.3 	Java 		Yes
application/x-java-applet;version=1.3.1 	Java 		Yes
application/x-java-applet;version=1.4 	Java 		Yes
application/x-java-applet;version=1.4.1 	Java 		Yes
application/x-java-applet;version=1.4.2 	Java 		Yes
application/x-java-applet;version=1.5 	Java 		Yes
application/x-java-applet;jpi-version=1.5.0_06 	Java 		Yes
application/x-java-bean 	Java 		Yes
application/x-java-bean;version=1.1 	Java 		Yes
application/x-java-bean;version=1.1.1 	Java 		Yes
application/x-java-bean;version=1.1.2 	Java 		Yes
application/x-java-bean;version=1.1.3 	Java 		Yes
application/x-java-bean;version=1.2 	Java 		Yes
application/x-java-bean;version=1.2.1 	Java 		Yes
application/x-java-bean;version=1.2.2 	Java 		Yes
application/x-java-bean;version=1.3 	Java 		Yes
application/x-java-bean;version=1.3.1 	Java 		Yes
application/x-java-bean;version=1.4 	Java 		Yes
application/x-java-bean;version=1.4.1 	Java 		Yes
application/x-java-bean;version=1.4.2 	Java 		Yes
application/x-java-bean;version=1.5 	Java 		Yes
application/x-java-bean;jpi-version=1.5.0_06 	Java 		Yes

[B]Shockwave Flash

    File name: libflashplayer.so
    Shockwave Flash 7.0 r69[/B]

application/x-shockwave-flash 	Shockwave Flash 	swf 	Yes
application/futuresplash 	FutureSplash Player 	spl 	Yes

```


Soo, everything LOOKS up and running, but evidently its not.

Any suggestions?](*,)

---

### Post by bruenig on 2007-01-16
What sort of problems are arises when you are installing flash 9? In my signature there is a link to deb packages and those should be sure things.

---

### Post by dothedorky on 2007-01-16
the installation goes smoothly, but when i visit certain sites, it tells me 'you need the latest version of flash player to view this file.'](*,)

edit: i followed your walkthrough, things went smoothly. However, mtv.com/overdrive says 'Express Install is not by this version of the flash player, please upgrade...'

---

### Post by artinla on 2007-01-16
> 
Shockwave Flash

    File name: libflashplayer.so
    Shockwave Flash 9.0 d78

MIME Type 	Description 	Suffixes 	Enabled
application/x-shockwave-flash 	Shockwave Flash 	swf 	Yes
application/futuresplash 	FutureSplash Player 	spl 	Yes
Totem Web Browser Plugin 2.16.2

    File name: libtotem-basic-plugin.so
    The Totem 2.16.2 plugin handles video and audio streams.

MIME Type 	Description 	Suffixes 	Enabled
application/ogg 	Ogg multimedia 	ogg 	Yes
video/mpeg 	MPEG video 	mpg, mpeg, mpe 	Yes
audio/wav 	WAV audio 	wav 	Yes
audio/mpeg 	MP3 audio 	mp3 	Yes
Helix DNA Plugin: RealPlayer G2 Plug-In Compatible (compatible; Totem)

    File name: libtotem-complex-plugin.so
    The Totem 2.16.2 plugin handles video and audio streams.

MIME Type 	Description 	Suffixes 	Enabled
audio/x-pn-realaudio-plugin 	RealAudio document 	rpm 	Yes


Not sure, I have it installed and it works fine.

I have the .deb but I don't know where I got it.  Why not use Automatix2 to install it?

Art

---

### Post by bruenig on 2007-01-16
your
```
about:plugins
```
even has it listed twice, you need to go into your /usr/lib/firefox/plugins directory and clear all the flash stuff out because it looks like you tried to install it anyway you could and now have 2 or 3 different versions in there. And once that is done, retry.

---

### Post by blowfish on 2007-01-18
> **bruenig said:**
> your
```
about:plugins
```
even has it listed twice, you need to go into your /usr/lib/firefox/plugins directory and clear all the flash stuff out because it looks like you tried to install it anyway you could and now have 2 or 3 different versions in there. And once that is done, retry.

if its any help i found the old flash plugin in my home directory(~/.mozilla/plugins/)

after i deleted that plugin the new version worked fine.

---

### Post by dolphinholmer on 2007-01-21
Navigate to /usr/lib/mozilla-firefox/plugins and delete all libflashplayer.so files.
Then go to [http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash)
and follow option 1

---

### Post by dothedorky on 2007-01-23
just an update: I navigated to usr/lib/mozilla-firefox/plugins and there are only two lib.so players.

in firefox's folder, there are a lot of scattered random .so files:

libgfxpsshar.so
libgkggx.so
libgtkembedmoz.so
libgtkxtbin.so

inside firefox is another plugin folder, which only contain two files.

the plain /usr/lib/mozilla/plugins only has one libjavaplugin.so inside.

SO basically i have 3 or 4 folders of which im not sure to delete.What should i be looking for?

I'm also a bit hesitant on deleting things, so id like to know if any of this can be reversed):P

---

### Post by dolphinholmer on 2007-01-23
Don't touch those files in the firefox folder.
It was only, and specifically, the *libflashplayer.so* file I suggested deleting.
Have you tried installing flash via the link I posted?

---

