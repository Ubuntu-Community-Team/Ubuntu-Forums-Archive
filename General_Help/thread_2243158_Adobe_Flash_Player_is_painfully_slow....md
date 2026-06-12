---
title: "Adobe Flash Player is painfully slow..."
date: 2014-09-06
forum: General Help
---

### Post by sillyboy on 2014-09-06
Hello,

Adobe Flash Player is running at about 1 frame every 8 seconds.  Audio is fine.  After reading stories about AFP and Linux I'm befuddled.  

Is there a way around AFP?  Do I need AFP?  Seems it was working, then it wasn't, then it was, then, then, then...

Please help?

Thank You  ;)


Ubuntu 12.04 precise

Linux 3.2.0-68-generic-pae

MoBo - M5A78L-M LX PLUS

CPU - AMD Athlon II X4 640 Processor

Video Card - Radeon HD 6570/7570

RAM - 8074 MBytes

---

### Post by EuclideanCoffee on 2014-09-06
Hm. Weird. Could you remove the plugin and reinstall it? From what I've heard, Chrome should have a built-in flashplayer you could try.

---

### Post by grahammechanical on 2014-09-06
You do not say what browser you are using.

[http://www.omgubuntu.co.uk/2014/01/chromium-npapi-flash-dropped-april-2014](http://www.omgubuntu.co.uk/2014/01/chromium-npapi-flash-dropped-april-2014)

Adobe stopped developing the Linux version of Flash a few years ago. 

[http://www.omgubuntu.co.uk/2012/02/adobe-adandons-flash-on-linux](http://www.omgubuntu.co.uk/2012/02/adobe-adandons-flash-on-linux)

You will find an installer for pepper flash in the software centre. Search for pepper flash.

Regards.

---

### Post by sillyboy on 2014-09-07
Hello'

I am using Firefox 32.0.  YouTube videos play fine, but when a embedded YouTube video is being played on a web page, it is choppy.  When I right click on the video it says that HTML5 is being used.  

Thank You

---

### Post by Toshiomi_Moriki on 2014-09-18
Hello, 
I encounted same trouble when I played some flash games.

My troubled system configuration is following;

Ubuntu 12.04.5 LTS
Linux 3.2.0-68-generic
DELL Inspiron mini12 (1210)
CPU - Intel(R) Atom(TM) CPU Z520   @ 1.33GHz
Video Card - Intel GMA500 (8086:8108:1028:02b1 rev 6)
RAM - 1024 MBytes
Flas plugin - 14.0.0.179 (/w pipelight)
Other - laptop mode

My solution is change the kernel backward.
It seems fine with 3.2.0-67-generic.

Lets try this. ;-)

---

### Post by Frogs Hair on 2014-09-18
If you are using the extension at the link check in preferences because there is a preference for keeping flash enabled except on the Youtube site. I have noticed that when I view embedded video it defaults to flash until I actually visit Youtube. 

[https://addons.mozilla.org/en-US/firefox/addon/youtube-all-html5/](https://addons.mozilla.org/en-US/firefox/addon/youtube-all-html5/)

---

