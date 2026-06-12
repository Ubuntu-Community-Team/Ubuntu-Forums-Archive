---
title: "System halt of my Xubuntu 13.04"
date: 2013-09-26
forum: General Help
---

### Post by raspatan on 2013-09-26
Dear, sometimes I get a halt of my system. In particular, I get a black windows with command lines saying many things. I don't know how to get that code. Using dmesg does not deliver the same code lines. The first time that I get that error in a session, I press CTRL + SHIFT + F7 in order to go back to my normal screen but then five minutes later or so I get the same crash but this time no command or other terminal (CTRL + SHIFT + Fx ) works.

Since I don't know how to get the code I took a picture of it. Here it is: [IMG]http://imgur.com/7jMPD1m[/IMG] [http://imgur.com/7jMPD1m](http://imgur.com/7jMPD1m)

I have no idea what the problem it is. There is a line that says: BUG: unable to handle kernel NULL pointer dereference at 0000000464 but google does not help with to find the problem.

Thank you very much!

Best.

---

### Post by raspatan on 2013-09-26
Ups, forgot to add that I get the crash report in Ubuntu saying that Xubuntu experienced an internal error.

The message says: 

Executable path: /usr/lib/gvfs/gvfsd-mtp
Package: gvfs-backends 1.16.1-0ubuntu1
Problem type: crash
Title: gvfsd-mtp crashed with SIGSEGV in LIBMTP_Read-Event()

and other information... I don't know how to export it! 

Sorry my noobness!

Thanks.

---

### Post by raspatan on 2013-09-26
Ok. I found this. [https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/1121285](https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/1121285) 

Apparently is an ongoing bug. However, I was not using Rhythmbox (to my knowledge). I actually have GMusicBrowser, not Rhythmbox. My message is slightly different though:

SegvAnalysis:
 Segfault happened at: 0xb73a804c <LIBMTP_Read_Event+28>:
 PC (0xb73a804c) ok
 source "0x4(%eax)" (0x00000004) not located in a known VMA region (needed readable region)!
 destination "%eax" ok
 Stack memory exhausted (SP below stack segment)
SegvReason: reading NULL VMA

---

### Post by raspatan on 2013-09-27
Any help is much appreciated. Thanks!

---

