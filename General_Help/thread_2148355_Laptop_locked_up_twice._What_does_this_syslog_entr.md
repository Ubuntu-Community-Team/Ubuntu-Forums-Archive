---
title: "Laptop locked up twice. What does this syslog entry mean?"
date: 2013-05-24
forum: General Help
---

### Post by Roasted on 2013-05-24
My laptop locked up twice within a 15 minute period. It's a Lenovo E430, 13.04, all latest updates. I looked in my syslog each time. The first time I wasn't sure what the error was, so I ignored it for that instance. Shortly after my laptop locked up again. Each time it happened when the laptop was sitting here, idle in my laptop, as I was "resting my eyes" for short bursts of time. Anyway, this is the error. Each one was the same.

May 24 21:45:28 JS-UbuE430 signond[2949]: ../../../../src/signond/signondaemon.cpp 360 init Failed to SUID root. Secure storage will not be available. 

What does this mean?

---

### Post by HiImTye on 2013-05-24
suid = set uid, which is a file permission allowing one user to run or access a file as the owner
http://en.wikipedia.org/wiki/Setuid

---

### Post by Roasted on 2013-05-24
> **HiImTye said:**
> suid = set uid, which is a file permission allowing one user to run or access a file as the owner
[http://en.wikipedia.org/wiki/Setuid](http://en.wikipedia.org/wiki/Setuid)

I'm familiar with set UID. I just wasn't sure over how this was the last item in my syslog before my system went into a hardlock on two occasions. It's happened maybe 8 times in the last month, but tonight in particular it was twice in a row.

---

### Post by Roasted on 2013-05-27
*bump*

Just happened again... same error in syslog. Anybody have any idea what I can do?

---

### Post by Roasted on 2013-05-29
Locked up again. Pretty awesome over here.

---

### Post by tgalati4 on 2013-05-29
I don't know anything about *signond*  but it looks like some sort of authentication framework:

tgalati4@Mint14-Extensa ~ $ apt-cache search signond
libsignon-glib-dev - library for signond - development files
libsignon-glib-doc - library for signond - documentation
libsignon-glib1 - library for signond
signon-keyring-extension - GNOME keyring extension for signond
signon-ui - Single Sign-on UI
signond - Single Sign On framework
signond-dev - Development files for Signon client library development
signond-doc - Single Sign On framework - documentation

And I have it installed Linux Mint Mate 14 (based on 12.10) but I don't see it running on my system, so perhaps it only runs during boot or login then exits completely.

Look for this file on your system:

../../../../src/signond/signondaemon.cpp

And more specifically, look at line 360 and see what it is trying to do.  Perhaps you have a missing or bad file that it is trying to access.

*signond* is a binary file in /usr/bin.  So it's possibly that you are getting a C++ stack trace that is pointing to a source file that does not exist on your system.  Unless you compiled it from scratch for some reason.

Perhaps your hard disk is having problems?

```
sudo smartctl -a /dev/sda
```

---

### Post by Roasted on 2013-06-05
I doubt it. It's a brand new SSD, but I'll run it through a smartctl long scan and see what happens.

EDIT - Another user I spoke to is having the exact same issues. It just so happens we have an identical GPU as well:

00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)

---

### Post by Roasted on 2013-06-07
Is anybody running 13.04 with a system packing a 2nd gen Intel Core processor? This seems to be the only similarity between my system and the one from another user who said they were having identical lockups. Can anybody confirm if they are or are not having any lock up issues? These issues are entirely random. I've had it happen when sitting idle or when in the middle of web browsing. The system is never hot, the fan is never running like crazy, and it's never in a position where I'm pushing it hard at all. Anybody?

---

### Post by Roasted on 2013-06-11
Fired up Linux Mint 15 but ultimately had the same results on day 2 of usage. :( I'm wondering if it's a kernel thing. I didn't have any issues with openSUSE 12.3, which uses kernel 3.7. I added both 3.7 and 3.9 to Ubuntu 13.04 but I cannot get my wireless working (Broadcom 43228), so I will likely not be spending much time on 3.7 or 3.9 until I can figure out the pesky Broadcom issue. Until then I got a slight 3.8 bump to .23. Curious if that will yield any positive results or not... 

Anyway, 2nd gen Intel Core users? Any insight? :D

---

### Post by tgalati4 on 2013-06-11
I'm running a 2nd gen Intel Core with integrated graphics, but only Linux Mint Mate 14 (which is 12.10) and it's rock stable.

---

### Post by ergosteur on 2013-06-18
I'm getting "signond[25526]: ../../../../src/signond/signondaemon.cpp 360 init Failed to SUID root. Secure storage will not be available." in my syslog too. However my system only temporarily locks up between 5 and 30 seconds, then runs normally again. 

Running 13.04 on a 1st-gen i7-based Xeon (Bloomfield) with NVIDIA Quadro graphics.

---

### Post by Roasted on 2013-06-19
Anybody who is having issues, hit up this bug report I posted and hit the "this affects me too" option. Also feel free to post details of your system and what you experienced. The more people having issues, the sooner this will be fixed, I'm sure.

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/1188774](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/1188774)

---

### Post by Roasted on 2013-07-07
Anybody have anymore input on this? I was doing so well for about 5 days. Absolutely no lockups. Then I got hit with one last night.

I wish I had the 5-30 lockup issue. One night when it locked up, I just plugged it in and let it go all night to see if it would recover. Nope. Still fully locked by morning. :(

---

