---
title: "What is a mythtv?how do I install it?"
date: 2007-01-18
forum: General Help
---

### Post by Coop on 2007-01-18
Hello
I'm not sure what this mythtv thing is,but I'm interested in it.Can you please tell me what is a mythtv,and how to install it?
Ahmed

---

### Post by blackened on 2007-01-18
MythTV is an interface for PC based personal video recording. It can also play music, recorded movies, and live tv. A bit similar to Windows Media Center. The project website is [http://www.mythtv.org]("http://www.mythtv.org").
Other similar projects are GeexBox and Freevo.

---

### Post by majoridiot on 2007-01-18
if you want to check out mythtv, then follow one of the guides here:

[https://help.ubuntu.com/community/MythTV](https://help.ubuntu.com/community/MythTV)

90% of the mythtv guides on the net are incomplete in some way, making for
nightmare installs.  i have followed these guides and had no problems installing 
myth on a frontend  with remote backend.

they are the most complete and accurate guides for ubuntu mythtv you will find.

---

### Post by Coop on 2007-01-18
Hello

Thank you for your kind answers.

First of all,is there a forum specifically for setting up mythtv on Ubuntu?

Second,I want to tell about my situation here:

1.I am using Ubuntu 6.10 GNOME,as you can see on the left side of my avatar.

I want to use my current desktop machine as both frontend and backend,and also as a normal desktop.

I think "MythTV Edgy Backend Frontend Desktop"[https://help.ubuntu.com/community/MythTV_Edgy_Backend_Frontend_Desktop]("https://help.ubuntu.com/community/MythTV_Edgy_Backend_Frontend_Desktop") is the perfect choice for me.

I will not be leaving this machine on all the time.

Most important of all,is it necessary to reinstall my system?

I would prefer it if I didn't have to reinstall my system.

These are my computer's specs:```
3 Ghz 64 bit/x86-64 Pentium 4 processor
1 GB RAM
200 GB hard disk space
ATI Radeon 9200 PRO with full 3d acceleration using Free Software Radeon drivers
WGT624 v3 wireless router working perfectly
And last but not least (drums roll) an Ubuntu 6.10 Edgy Eft (GNOME) 32-bit edition and Windows XP Professional dualboot


```

Its a pretty powerful computer in my opinion.

Are these specs powerful enough to run Mythtv?

What other hardware do I need?

And again,most important of all,I do not want to reinstall my system unless its absolutely necessary.

I just want to transform my existing desktop into a Mythtv.

I am looking forward to installing Mythtv.

Please answer me

Ahmed

---

### Post by Titus A Duxass on 2007-01-18
This depends, if you have, in your existing system, a separate /home partion then you may have to reinstall  or at least you may lose the data in the home partition.

Alternatively, if you have an existing /home you can do a mythtv install with your existing user and during the install the user mythtv will be created.

With this set-up you can get mythtv to log-in automagically and use mythtv as your normal access.

The disadvantage with this is that using ext2 or 3 (which is the normal set-up) may lead to problems deleting large files.

If you do not have a separate /home and therefore have everything on / you should be able to follow the How-To and not have to reinstall.

---

### Post by reclusivemonkey on 2007-01-18
> **Coop said:**
> 
I will not be leaving this machine on all the time.


If you want to use MythTV for recording tv programs, then it won't record anything if its not turned on.

---

### Post by Coop on 2007-01-18
Hi
When I say I that I will not be leaving this machine on all the time,I mean that I will keep the machine on when tv shows I want to record are coming,and I will turn the machine off when I don't need to do anything.
Ahmed

---

### Post by Titus A Duxass on 2007-01-18
I have a dedicated frontend/backend that I leave on 24/7 unless I'm away for an extended period of time.

---

### Post by majoridiot on 2007-01-18
> **Coop said:**
> These are my computer's specs...

those specs look quite good... although you made no mention of how much
free space you have on the HD.  livetv and recorded programs take up A LOT
of HD space, unless you transcode them.

> **Coop said:**
> What other hardware do I need?

you do not specify how you want to get the tv signal into the computer.
if you want to take it directly from the cable or antenna, then you will
need a video capture card.  a good, reasonably inexpensive card is
the hauppauge pvr-150.  i run one and it works very well.

if you have a cable or satellite box with a firewire connection, and your
computer has 1394 capability, then it *might* be possible to get 
your tv input directly through a firewire connection.  i have firewire on
mythtv as well, controlling a motorola DCT6212III cable stb.

---

### Post by Coop on 2007-01-18
Hello

I have reinstalled Ubuntu according to this guide [https://help.ubuntu.com/community/MythTV_Edgy_Backend_Frontend_Desktop]("https://help.ubuntu.com/community/MythTV_Edgy_Backend_Frontend_Desktop")

My Ubuntu side of my hard disk has lots of free space.

I created a 40 GB xfs partition for the tv stuff,and I store all my large files on my Windows XP NTFS partition using ntfs-3g

Also,how do I know how much free space I have on my hard disk?
The Computer thing in the Places menu doesn't show how much I have.

And also,I don't understand how to get the tv signal into the computer.
I'll ask someone to help me for that part.

Ahmed

---

### Post by majoridiot on 2007-01-18
> **Coop said:**
> And also,I don't understand how to get the tv signal into the computer.
I'll ask someone to help me for that part.

Ahmed

> **majoridiot said:**
> you do not specify how you want to get the tv signal into the computer.
if you want to take it directly from the cable or antenna, then you will
need a video capture card.  a good, reasonably inexpensive card is
the hauppauge pvr-150.  i run one and it works very well.

if you have a cable or satellite box with a firewire connection, and your
computer has 1394 capability, then it *might* be possible to get 
your tv input directly through a firewire connection.  i have firewire on
mythtv as well, controlling a motorola DCT6212III cable stb.

;)

---

### Post by Coop on 2007-01-18
Thank you majoridiot.
I mean that I'll ask my relative to help me install the video capture card and other hardware,as I don't know how to do hardware stuff.
Ahmed

---

### Post by Coop on 2007-01-19
What's 1394 capability?Please answer me.
Ahmed

---

### Post by majoridiot on 2007-01-19
if you go with a pvr series or other ivtv-based capture card, i recommend you follow this
guide for installation:

[https://help.ubuntu.com/community/Install_IVTV_Edgy](https://help.ubuntu.com/community/Install_IVTV_Edgy)

> **Coop said:**
> What's 1394 capability?Please answer me.
Ahmed

IEEE1394 == firewire

---

### Post by Coop on 2007-01-19
Thank you majoridiot for helping me.
I'm going to install mythtv as soon as I get a video capture card and/or a firewire connection.
Ahmed

---

