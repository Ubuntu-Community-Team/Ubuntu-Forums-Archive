---
title: "New to Ubuntu - Various Issues"
date: 2013-09-05
forum: General Help
---

### Post by Porynog on 2013-09-05
Hi, I'm fairly new to the whole Linux thing, I just switched from Windows and for the most part, I'm satisfied with it. However there's a few big issues I'm dealing with.

1. The program Audacity barely works in it, I frequently use Audacity as a musician, but I can't seem to more than two actions until it freezes or crashes.

2. Adobe Flash doesn't work right at all. I try to adjust settings on sites like Tinychat, Omegle, etc anything really, and I can't even click anything. Shouldn't a program as commonly used as Adobe Flash work in Ubuntu? 

3. Burning CD's doesn't want to work, I'm wasting CD's because of it.

Any help would be appreciated.

---

### Post by Petro Dawg on 2013-09-05
Welcome the Linux world.  

Unfortunately we will need more information before being able to give much assistance.

First, which version of Ubuntu are you using? 

Next, what are your computer specifications, most importantly processor type and amount of RAM you have installed? 

Also what program are you using to try to burn CD's? Some programs are known to work better than others.

Perhaps someone else can help you with your Adobe flash issues, it appears there is a flash player download available for Linux ([http://get.adobe.com/flashplayer/otherversions/](http://get.adobe.com/flashplayer/otherversions/)).  Have you installed adobe flash player?  If so, how?

---

### Post by Kirk Schnable on 2013-09-05
> **Porynog said:**
> 1. The program Audacity barely works in it, I frequently use Audacity as a musician, but I can't seem to more than two actions until it freezes or crashes.
I don't frequently use Audacity myself, but I have seen it used on our Linux machines at work fairly often.  I've never encountered any freezing issues with Audacity.  We may need to help you dig through some log\debug output to figure this out. 

> **Porynog said:**
> 2. Adobe Flash doesn't work right at all. I try to adjust settings on sites like Tinychat, Omegle, etc anything really, and I can't even click anything. Shouldn't a program as commonly used as Adobe Flash work in Ubuntu?
How did you go about installing Flash?  We have it installed on our computers and it's working fine.  We installed it from apt by running
```
sudo apt-get install flashplugin-installer
```

> **Porynog said:**
> 3. Burning CD's doesn't want to work, I'm wasting CD's because of it.
> **Petro Dawg said:**
> Also what program are you using to try to burn CD's? Some programs are known to work better than others.
I'll second Petro Dawg's question.  I typically use xfburn or Brasero. 

Kirk

---

### Post by Porynog on 2013-09-05
I have the latest version and i tried to enter that code but it then proceeded to ask me for my password, which it wouldn't let me type.

---

### Post by Petro Dawg on 2013-09-05
Keep in mind, for security purposes, when you type a password in terminal, it will not appear in the terminal. Even though you see nothing on the screen, it is still reading your keystrokes.

Also, if you want help with your other issues, you will need to answer the questions I asked before.

---

### Post by Porynog on 2013-09-05
I'm not even sure tbh because I just got a new hard drive from my friend

---

### Post by Petro Dawg on 2013-09-05
I'm afraid I can't follow what you are typing.  :confused:

The age and/or condition of your hard drive has no influence on the version of Ubuntu you have installed, amount of RAM installed, Processor type, or the program you used to burn CDs.  I'm pretty sure the state of your hard drive is the one thing no one asked about.

---

### Post by Porynog on 2013-09-05
Yeah that's the thing, I don't know most of that stuff. I tried Rhythmbox and the "CD Burner" thing to burn CD's before, rhythmbox didn't work and CD burner just gave me white noise. I tried to download both CD burning programs listed previously and both of them were just folders with like 100 different files in them. It's not like, complicated things I want. and I have no idea how to even navigate ubuntu to find out the properties of my computer. I also tried to download Flash, and I already have that version, it just won't work right. It should be clickable when you have the options menu of it on websites, it works fine on Windows

---

### Post by Petro Dawg on 2013-09-05
OK, I think I understand the situation now.

If you are running Ubuntu 12.04, you should be able to click on the "gear like" symbol on the upper right hand corner of the screen and get to an option labeled "System Settings"

from there, click on "Details", it will have most of the info I was asking for

---

### Post by Porynog on 2013-09-05
Ubuntu 13.10
Memory 3.9 GiB
Process Intel® Pentium(R) CPU B960 @ 2.20GHz × 2 
Graphics Intel® Sandybridge Mobile x86/MMX/SSE2
OS type 32-bit
Disk 74.5 GB

---

### Post by Petro Dawg on 2013-09-05
13.10, no wonder you are having issues...

I think that is the beta test version for the release to come out next month

---

### Post by Porynog on 2013-09-05
Is there ever going to be a point where this actually works?

---

### Post by buzzingrobot on 2013-09-05
First, you need to learn to use Ubuntu rather than do things at random, as you appear to be doing.

Second, Ubuntu provides a Software Center program which allows you to search/browse for software and install and remove it.

When you say you downloaded something but it was only a folder with 100 files in it, you apparently downloaded and clicked on an archive.  Doing that will extract but not install the archive's content.

Brasero is the CD/DVD tool installed in Ubuntu. It works.  Others are available via Software Center.

No one knows what you mean by "white noise".

Flash is part of a package called "Ubuntu Retricted Extras" available via the Software Center app. If you downloaded it from another source it is likely installed incorrectly.

Ubuntu doesn't work like Windows. You should take time to read the docs and learn how to use it.

(EDIT: You seem to be using 13.10.  Correct? That's an unreleased version that is only available for testing. As such, it changes constantly. If it works reliably, you are lucky.  Get 12.04.03 LTS or 13.04 and install that. No one can really help you with 13.10.)

---

### Post by Petro Dawg on 2013-09-05
> **Porynog said:**
> Is there ever going to be a point where this actually works?

Yes, after it is officially released.  But it will be buggier than rotten wood till then.

I strongly encourage those new to Ubuntu to install a "Stable" version of Ubuntu, such as 12.04LTS (preferred), or at the very least 13.04.

---

### Post by Porynog on 2013-09-05
> **buzzingrobot said:**
> First, you need to learn to use Ubuntu rather than do things at random, as you appear to be doing.

Second, Ubuntu provides a Software Center program which allows you to search/browse for software and install and remove it.

When you say you downloaded something but it was only a folder with 100 files in it, you apparently downloaded and clicked on an archive.  Doing that will extract but not install the archive's content.

Brasero is the CD/DVD tool installed in Ubuntu. It works.  Others are available via Software Center.

No one knows what you mean by "white noise".

Flash is part of a package called "Ubuntu Retricted Extras" available via the Software Center app. If you downloaded it from another source it is likely installed incorrectly.

Ubuntu doesn't work like Windows. You should take time to read the docs and learn how to use it.

Brasero is actually what I tried to use earlier now that I searched for it, it didn't work and it gave me white noise (it didn't burn what I wanted, to be more precise)
Installing Restricted Extras now, will tell if that works or not.

---

### Post by buzzingrobot on 2013-09-05
If you are still on 13.10, there's no guarantee anything will work.

---

### Post by Petro Dawg on 2013-09-05
Your "friend" did you and the Ubuntu community quite the disservice by giving you an unstable test version to try out as your first look at Ubuntu.  You, as a newbie to Ubuntu, should not be using that version.  You'll will most likely never get it working to your liking, and you will probably give up on Linux as a whole because of your experience with it.  

If you really want to learn about Ubuntu, start by installing a stable version.

---

### Post by buzzingrobot on 2013-09-05
Go here: [http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop) and download and install from there. Then, folks can help.  13.10 changes from day to day, and will until it is released. Brasero might be broken in it today, and fine tomorrow, and broken on Saturday.

---

