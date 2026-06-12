---
title: "[SOLVED] Frustrated with gxine HELP!!!!!"
date: 2007-10-31
forum: General Help
---

### Post by ccmccm on 2007-10-31
ok ive really tried and tried to get my dvd and video files to work.  I am using gxine 0.5.11 I read this page [https://help.ubuntu.com/7.04/musicvideophotos/C/video.html#video-dvd](https://help.ubuntu.com/7.04/musicvideophotos/C/video.html#video-dvd) saying to install libdvdcss2, libdvdnav4, libdvdread3, libdvdplay0. I installed all but libdvdplay0, i cant find it. I have w32codecs installed as well.  when i insert a dvd gxine auto opens and gives the error message 'no demuxer found - stream format not recognized' I am running Ubuntu 7.10 and am frustrated so far Please Help!!

---

### Post by linuxwizard on 2007-11-01
Do a search in Synaptic for libdvdplay0 to see if it is installed I think that gets installed with another package. Try installing libxine1-ffmpeg you should need it also.

[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

---

### Post by markharding557 on 2007-11-01
> **ccmccm said:**
> ok ive really tried and tried to get my dvd and video files to work.  I am using gxine 0.5.11 I read this page [https://help.ubuntu.com/7.04/musicvideophotos/C/video.html#video-dvd](https://help.ubuntu.com/7.04/musicvideophotos/C/video.html#video-dvd) saying to install libdvdcss2, libdvdnav4, libdvdread3, libdvdplay0. I installed all but libdvdplay0, i cant find it. I have w32codecs installed as well.  when i insert a dvd gxine auto opens and gives the error message 'no demuxer found - stream format not recognized' I am running Ubuntu 7.10 and am frustrated so far Please Help!!
have a look at [http://www.getautomatix.com/]("http://www.getautomatix.com/") this will install everything for you

---

### Post by linuxwizard on 2007-11-01
ccmccm
Before you consider using automatix do research on it first than decide if you want use.

Please note that Automatix2 is a third-party utility, developed and maintained independently by the Automatix Team and [COLOR="Red"]is not supported nor recommended by Ubuntu[/COLOR].
[https://help.ubuntu.com/community/Automatix](https://help.ubuntu.com/community/Automatix)

---

### Post by markharding557 on 2007-11-01
ive never had any issues with automatix ive only used it to install codecs though

---

### Post by francie on 2007-12-26
Thanks to this forum I fixed a problem I was having with gxine running dvds.
I recieved a message 
"The xine engine failed to start. No demuxer found - stream format not recognized"

I followed the instructions in: [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

But this does not install , libdvdnav4, libdvdread3, or libxine1-ffmpeg you.

When I installed these my problems went away.

---

### Post by jslmg on 2008-01-09
I've installed all packages here:

[http://ubuntuforums.org/showthread.php?t=622617&highlight=gxine](http://ubuntuforums.org/showthread.php?t=622617&highlight=gxine)

but still can't get sound from streaming radio stations. Sometimes the player connects, but i get an error window saying I'm missing "cook.so" (for BBC World Service, for example) or I'm missing "sipro.so" (for BBC News Summary). Where do i get these libs, plus any others I might encounter?

---

### Post by jslmg on 2008-01-09
OK, the thread is once again [SOLVED]. I got w32codecs, and all was resolved, for now.

---

### Post by jslmg on 2008-01-12
Sorry, not solved, again.

Can anyone help me, then, with these two issues:

1) When listening to a .ram stream such as BBC World Service, the stream plays for about 2 minutes, then stops. That's not the case in Mac OS X, which is on the same computer and using the same Internet connection.

2) Video streams, such as VOA TV or NASA, crash Gxine as they start.

---

