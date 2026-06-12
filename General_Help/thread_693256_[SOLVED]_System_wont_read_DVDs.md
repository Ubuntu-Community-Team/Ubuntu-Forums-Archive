---
title: "[SOLVED] System wont read DVDs"
date: 2008-02-10
forum: General Help
---

### Post by fullmetalgerbil on 2008-02-10
I recently reinstalled Ubuntu 7.10. For some reason it is not reading DVDs-actually, to be more specific it isn't reading DVD movies. I've installed a whole mess of codecs and still nothing works-no desktop icon when I load the DVDs, nothing. Its not a hardware problem, the drive spins and everything was working prior to the reinstall, plus it reads DVD data discs with no problem.
 I know I must be missing something somewhere but to the best of my knowledge I've got all the codecs I had last time when it was working-and even when I *didn't* have the right codecs last time it still at least gave me a desktop icon showing that it was reading the disc.
Basically, I'm flummoxed.

---

### Post by seventhc on 2008-02-10
have a look here
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

or

[http://ubuntu.wordpress.com/2005/12/04/libdvdcss2-and-w32codecs-for-ubuntu/](http://ubuntu.wordpress.com/2005/12/04/libdvdcss2-and-w32codecs-for-ubuntu/)

---

### Post by jrusso2 on 2008-02-10
Add this to your reading list

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by fullmetalgerbil on 2008-02-10
Yeah, well, I went there and it was just about installing the restricted extras package which I already have installed. Thanks anyways, though.

---

### Post by fullmetalgerbil on 2008-02-10
Wait, let me try the medibuntu stuff..

---

### Post by MissShona on 2008-02-10
I had a similar problem;  Here's what I did to get it working:  

>  I was getting some sort of error about *"no plugin to handle /dev/sda0"* or something or other. Then I found out I just needed to go to:

**Add/Remove Programs** then go to **Multimedia** and there was a place to choose the Xine codecs for installation.

Ok, then my problem became...

*You do not have the proper permissions....disk not loaded*

...or something like that.

Then I found out that you need to install a special library in order to play commercial DVDs; so I went to the terminal and typed:

**apt-get install libdvdcss2**.

Funny...I did that at first, but got tons of errors and it would not install. The problem is you have to install the Xine codecs first!

What application are you using to play DVDs?  Which error is it giving?  With me, even reading the tutorials given by [http://www.medibuntu.org/]("http://www.medibuntu.org/") to the tee did not help me (I have Kubuntu Feisty Fawn).  Remember, the system add/remove programs is your safest bet sometimes when you need entire repositories.  Make sure the specific xine codecs (if you are using xine & Kaffeine) are the ones that are installed.

Good luck to you :) !

---

### Post by fullmetalgerbil on 2008-02-10
I'm trying to use VLC. Its not even giving me an error mesage, its just not recognizing the DVD at all.

---

### Post by fullmetalgerbil on 2008-02-10
Also, I have the xine codecs, w32 codecs, and libdvdcss2 installed.

---

### Post by ubuntu-freak on 2008-02-11
Try part 1 and 3 of my [how-to](http://ubuntuforums.org/showthread.php?t=661833). Part 1 will skip anything you already have, and part 3 will make vlc default for dvds, not just enable encrypted playback.
 
Nathan

---

### Post by raddellee on 2008-02-12
Heres what i did to get it working

sudo apt-get install: ( individually )


libdvdcss2

libdvdnav4

libdvdread3

lame

w32codecs

flashplugin-nonfree

xine-ui


If this fails try these. Or you can try M player. As an after thought 


---add remove  

GStreamer Dirac video plugin

GStreamer extra plugins

GStreamer ffmpeg video plugin

GStreamer fluendo MPEG2 demuxing plugin

GStreamer plugins for aac, xvid, mpeg2, faad

GStreamer plugins for mms, wavpack, quicktime, musepack

---

### Post by fullmetalgerbil on 2008-02-12
Got it working, thanks for all the help everyone.

---

### Post by ubuntu-freak on 2008-02-12
Great! What was the problem? Just curious.
 
Nathan

---

### Post by fullmetalgerbil on 2008-02-12
The system wouldn't read dvds, that was the problem. The computer was about to crap out anyways, I got another one today and followed the instructions on this thread and every thing works fine. Well, except for the fact that I set VLC as my default player and it still goes to totem as the default. But I can live with that.

---

### Post by ubuntu-freak on 2008-02-12
> **fullmetalgerbil said:**
> The system wouldn't read dvds, that was the problem. The computer was about to crap out anyways, I got another one today and followed the instructions on this thread and every thing works fine. Well, except for the fact that I set VLC as my default player and it still goes to totem as the default. But I can live with that.

 
Try gconf-editor again. Remember to right click and set as default.
 
Nathan

---

