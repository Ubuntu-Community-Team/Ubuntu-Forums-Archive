---
title: "Audio missing in Flashplayer"
date: 2007-10-29
forum: General Help
---

### Post by pi6502 on 2007-10-29
Hi,

I've posted this problem here [http://www.linuxquestions.org/questi...283/page2.html](http://www.linuxquestions.org/questi...283/page2.html) some time ago. I have no sound when I playback flash clips - although every other sound on my PC is working (mp3 and the like).
I did not fix it as I don't know how to downgrade ALSA or the Flashplayer itself with Synaptic.
I posted this when I was using ubuntu 7.04; it's quite annoying that I find the problem still to exist in the 7.10. Is it because I have an old soundcard maybe?

It seems I'm using the ALSA 1.0.14 driver and the Shockwave Flash 9 r48 player.

How do I downgrade - using Synaptic Package Manager - either ALSA or Flashplayer? Where do I get older packages and how do I install them with SPM?

Thx

---

### Post by daengbo on 2007-10-29
Youir link is broken so I can't read the details of the problem, but it sounds like you have one of the old library problems with Flash.

I thought that newer Flash players had gotten rid of the problem completely. Can you check that you are using the system plugin and not one that was installed in your local home, perhaps some time ago?

Please check this page for help: [http://wiki.ubuntu.com/FlashPlayer9](http://wiki.ubuntu.com/FlashPlayer9)

Click on [this link]("apt:flashplugin-nonfree") to make sure that the appropriate Flash is installed.

Please check your user plugins, the referenced page, and the URL. If those don't solve the problem, please let me know.

---

### Post by pi6502 on 2007-10-31
I am using the flashplugin-nonfree 9.0.48.0.2+really0ubuntu12(gutsy). I've checked this by looking at Synaptic and by looking at Firefox.

My 7.10 is freshly installed, just a couple of days old.

In the meantime, I tried this [http://www.macewan.org/2006/06/01/howto-firefox-flash-video-sound-on-ubuntu-linux-dapper/](http://www.macewan.org/2006/06/01/howto-firefox-flash-video-sound-on-ubuntu-linux-dapper/) but without success.

The page at [http://www.linuxquestions.org/questions/ubuntu-63/no-audio-with-flash-player-562283/page2.html](http://www.linuxquestions.org/questions/ubuntu-63/no-audio-with-flash-player-562283/page2.html) is reachable. I suppose it is related to either ALSA driver or the flash plugin. Older versions of both (i.e. in older distros) worked fine with me.

---

