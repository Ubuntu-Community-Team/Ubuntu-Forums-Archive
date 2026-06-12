---
title: "a program to edit mpeg video"
date: 2007-09-02
forum: General Help
---

### Post by clinto on 2007-09-02
BEFORE YOU POST let me explain what I'm trying to do.

I have a Sony camcorder that records in MPEG(I'm kind of disappointed, I thought it would record into DV format). Every time I start and stop recording on the camera, it creates a new MPEG file. I want to be able to edit bits and parts of each MPEG, join some together, maybe add some text, and then convert everything to dvd format so that it will be able to play in a stand-alone player.

IF YOU SAY KINO I'LL HIT YOU WITH A BRICK! j/k Kino allows you to edit DV files. I've been trying to read over SOOO many threads and people keep throwing around Kino when it's obviously not the answer.

The closest thing I've seen talked about was Avidmux, Cinerella, and Kdenlive. Avidmux's description says that it's used to edit AVI(divX) files. From what I've read about Cinerella, people are saying it causes a lot of conflicts. Kdenlive sounds half way decent, but I'm not running a KDE desktop environment, I'm running Gnome.

I started using DeVeDe, it's a nice little program, but it doesn't allow you to edit files. It only lets you add MPEG files together to make a multi titled/chaptered video. I'm thinking I would like to use another program to edit the files first, then I could use DeVeDe to put them all together.

[rant]
THERE MUST BE SOMEONE OUT THERE THAT HAS DONE THIS! It seems the only people who respond to specific problems on these forums are people who haven't had experience themselves. I know the mind set of those-of-you who look at people who complain about a response as undeserved whiners, and I agree in most cases. But I can't count how many threads I've come across where I'm trying to figure out a problem only to find people being criticized for being frustrated. When you respond to a person's post, you're not just helping the person that posted it. I've been trying to do what's right and search these forums before posting, but all I find are either responses from people who don't have any experience with the problem, or they do a piss poor job of explaining it so that people other than them selves can understand it, or they bicker with a person over frustration, or they just don't answer at all. These forums would be great if they weren't polluted by people who don't know what they're talking about.
[/rant]

I've tried looking over a few how-tos as well and I haven't found anything helpful. Keep in mind, I've never actually done any video editing before. This is all new to me in every way. I apologize for the long post. Any helpful responses would be SO appreciated. However, the more threads I read, the more skeptical I become about the help these forums actually provide.

---

### Post by reckless2k2 on 2007-09-02
if your looking for good video editing, you'll have to do it in windows. linux weaknesses are in video editing and gaming.

---

### Post by vanadium on 2007-09-02
Avidemux will do perfectly to join or split mpeg files.

---

### Post by clinto on 2007-09-02
Okay, I'm trying the Avidemux. It seems to be a decent program. I just don't know what the hell I'm doing. Does anyone have experience with this program? I'll google around in the meantime.

I went to the help section in the program but there was only this:

[[img]http://pix.nofrag.com/b/4/c/4f3100705a1903c50b1f89a9855d9.png[/img]](http://pix.nofrag.com/b/4/c/4f3100705a1903c50b1f89a9855d9.html)

I have no idea what that means. Are those codecs? What does it mean to have support for it? Does that mean it will not do everything correctly without those items? And what does it mean to recompile it?

I'm surprised programs like these don't have tons of help files.

---

### Post by Amazona aestiva on 2007-09-03
See the first link in my signature. There You can find avidemux, codecs... etc. etc.
Good luck!

---

### Post by cwaldbieser on 2007-09-03
If you get the ffmpeg package:

```

$ ffmpeg -i movie.mpeg -target dv movie.dv

```

This converts mpeg movies to dv format so you can use kino.

---

### Post by clinto on 2007-09-03
Thanks guys.

I'm slowly learning how to use Avidemux. I'm missing some hair, but I'm learning.

My current problem is figuring out the aspect ratio. I'm using the auto>dvd feature and it asks for the source and destination's aspect ratio. Everything I try ends up making the video stretched tall ways. I'm not sure how to determine the source's aspect ratio. I could check the camera I guess. I tried reading the wiki for information on this, but to my luck it doesn't cover it in depth. It even mentions that there is content needed there.

---

### Post by clinto on 2007-09-03
Well, I just opened the flip face on my camcorder and realized it says 16:9 in the bottom corner. However, I tried doing 16:9 to 16:9 the first time and it displayed incorrectly.

---

### Post by Tomlin on 2007-10-08
My card (PVR-150) captures in mpeg. I'm trying to edit out commercials from a  basketball game using Avidemux and I'm having problems. At the 15 minute, 53 second mark, fading back in from black to the game, all the sound is gone. From there until the end (1:38:33) there is video, but no sound. Anyone else having this problem?

I didn't mean to hijack your thread, but other than this (rather large) problem, Avidemux is just what I'd been looking for.

---

