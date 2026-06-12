---
title: "MP3 Player for Linux"
date: 2008-03-01
forum: General Help
---

### Post by wookietim on 2008-03-01
I am in the market for a new MP3 Player (I got my tax return and my yearly "Gadget frenzy" is upon me). I love the look and UI of the iPod, but the fact that iTunes isn't really happy with Linux is a limiting factor there....

Right now, I am salivating over the Creative Zen 8 GB MP3 Player (The memory is right - I am stuck in the 80's, so my music needs aren't big and the look is nice. Plus I liked my older creative zen player a lot...). Is this easy to use with Linux?

What I want is this : Mainly I need it easy to copy music. That is usually not a real problem, since at the worst these MP3 players look like a USB drive that I can drag and drop files onto. BUT, since the newer player do video as well, I'd like to be able to easily put video on it too. This is where Linux tends to let me down (Well, not Linux per se... read on).

The software that is out there is made for Windows/Mac. It tends to choke when running under WINE and there are no versions for Linux. I need a player that can deal with copying video under Linux as well as music.

Would the little, expensive piece of molded plastic I am looking at work for that? Are there any other suggestions?

---

### Post by gobbles414 on 2008-03-01
Hi wookietim,

Although Apple is the new Microsoft, you should be able to use your iPod as you describe in Linux. An application that looks good for managing both audio and video for iPods in Linux is [Floola]("http://www.floola.com/"). Floola also works in Windows and OS X, I believe. Does that help?

---

### Post by jmc1024 on 2008-03-01
I just bought the Sansa e270 (6 gb), $114 from new egg.  For just playing music and podcasts and for carrying around files, it's been perfect for me.  It even displays the album cover artwork. I use rsync to keep the device up to date.  As for videos, I am not interested in them, but I've seen a script or two that is supposed to convert them to the proper format.  I could try a test if you really want me to.

Mark

---

### Post by wookietim on 2008-03-01
I'll have to check out Floola... Does it make it easy to get video onto the player?

---

### Post by gobbles414 on 2008-03-02
> **wookietim said:**
> I'll have to check out Floola... Does it make it easy to get video onto the player?

I barely have enough room for my music collection on my iPod, so I haven't had to worry about videos on my iPod! :lolflag: I haven't experimented with Floola beyond installing it and exploring the user interface for a few minutes. There's actually a user called Floola here in the forums. I don't know if he/she is the developer of Flooa, or just a fan. But he/she might be worth seeking out for further advice. Let me know how you progress.

---

### Post by 3rdalbum on 2008-03-02
I have a Sony Walkman - NWZ-A618F, I think it is. It's drag 'n' drop for music, which makes it Linux-compatible. You can use ffmpeg from Medibuntu in order to encode videos for it, or use Blacklight (my GUI frontend for encoding videos for the Walkman, requires either Medibuntu's ffmpeg or an svn version with full support configured into it).

---

### Post by chewearn on 2008-03-02
One thing to check when buying a portable media player (for use with Linux) is whether it supports USB mass storage device, or not.  Some recent players (e.g. Creative Zen Vision) might support USB MTP only, rather than USB mass storage.  The way to check: does the specs (on the box) specifically mentioned Windows, or Windows Media Player as mandatory requirement?

I was a long time user of Creative MuVo devices (owned three successive devices); it doesn't have the cool guy iPod UI, nor support video (no LCD panel).  But it got solid MP3 playback, and you don't have to install the crapware that comes with it (since it's USB mass storage, you can drag and drop via any file manager).

I recently borrowed a Creative Zen Vision from a friend, for watching video while traveling on a long bus trip.  It was a pain to copy video files into this device.  It's MTP only, so you need to install MTP support in Linux, then use the outdated nomad2 apps, which crash left and right.

---

### Post by wookietim on 2008-03-02
I used to really like my RCA Lyra - it didn't do video, but it was an 8 gb music player and seemed to be happy with whatever OS I threw at it... But, alas, after 3 years of hard use, it seems to have bit the dust, so I am definitely looking...

---

### Post by Islington on 2008-03-02
Holy ****! all of this companies mp3 players are expressly compatible with linux!

[http://www.trekstor.ch/en/products/detail_mp3.php?pid=74](http://www.trekstor.ch/en/products/detail_mp3.php?pid=74)

scroll down to the communication with pc section.

anyone have any experience with these players?

---

### Post by gobbles414 on 2008-03-02
> **Islington said:**
> Holy ****! all of this companies mp3 players are expressly compatible with linux!

[http://www.trekstor.ch/en/products/detail_mp3.php?pid=74](http://www.trekstor.ch/en/products/detail_mp3.php?pid=74)

scroll down to the communication with pc section.

anyone have any experience with these players?

Cool! I don't have experience with any of these devices. But I'm sure willing to give the benefit of the doubt to any company that's actively supporting Linux in its hardware. :guitar:

---

### Post by wookietim on 2008-03-02
There is only one problem with the threkstor - they look great and they seem to (at least advertise) Linux compatibility... But nowadays, if I am going to pay $200 for a player, it had better do video and these don't seem to support that...

---

### Post by Auslegung on 2008-03-07
> **wookietim said:**
> There is only one problem with the threkstor - they look great and they seem to (at least advertise) Linux compatibility... But nowadays, if I am going to pay $200 for a player, it had better do video and these don't seem to support that...

Here's what it says under Downloads: Tool for converting movie files for TrekStor blaxx using Microsoft Windows. In order to play movie files on TrekStor blaxx you must convert them to SMV file format. The converter will convert a large variety of video files (AVI, MPG, WMV) into SMV-file format.

Seems to do videos.

---

### Post by wookietim on 2008-03-07
I hadn't noticed that - the trekstor players I found on Amazon and E-Bay don't have video capability...

---

### Post by Afkpuz on 2008-03-07
Well, I'm not sure how badly you want a current mp3 player, but I use a toshiba gigabeat f20 with rockbox on it.  Rockbox works like a drag and drop player, so once you've ripped your CD, you just drag the folder onto your mp3 player (which shows up like a hard drive) and you're good.  I'm sure that gigabeats would be cheap on ebay and they can go up to 40 gigs I think in the F series.  

If you don't go with that, I highly recommend using rockbox on whatever player you end up buying.

Rockbox for the f20's supports video playback, but you must encode your video down to the rockbox resolution.

---

