---
title: "[SOLVED] strange behaviour launching firefox and gnucash"
date: 2008-06-13
forum: General Help
---

### Post by Hugo74 on 2008-06-13
Hi all,

I'm already using (k)ubuntu for a few years, but it's the first time that I have really strange behaviour in some applications. Currently I've Kubuntu 8.04 with KDE 3.5.9 and 4.0.5 installed parallel and using the latest kernel (2.6.24-18) and all available updates.

Since a few days I can not use Firefox 3 and Gnucash anymore because when I start them they need ages (some minutes) to launch. When they are up and running I still can not use them because at every click the programs do not respond anymore for another few minutes. 

I already tried reinstalling Firefox, using a new profile and the safe mode. It's the same every time :-(

The started programs do not put any load on the CPU, and there is definitly no problem with not enough memory. And I don't have any problems with starting other programs, even Firefox 2 works fine.

Does anyone else have this problem or at least a solution for it?

I would highly appreciate any help!

Cheers
Hugo74

---

### Post by editrix on 2008-06-14
I'm replying mainly to bump, because I had the exact same behaviour with FF. Never tried GNUcash.

I'm also wondering if this is a problem specific to Kubuntu, because I couldn't get an answer when I posted.

Have you tried Kmymoney? I ask because I see it uses different libraries, and the problem may be in one of the libraries.

---

### Post by Hugo74 on 2008-06-14
Thanks for replying, yes I tried KMoney as well and it works fine. Usually I try to stick with KDE applications but I prefer Gnucash to handle my finances.

Someone else experiencing this problem? Or can at least someone give me hints on how to track it down to create a proper bug report?

---

### Post by editrix on 2008-06-14
Trying to fix some other problem, I went into Gnome and disabled gdm in the system administration box. I had KDE set to use kdm. After that, I experienced the same behaviour with startupmanager, which had worked fine before.

So I think it is a bug in Kubuntu handling gnome programs--although how FF connects to that I don't know. Other than trying out a whole bunch of programs we don't use, though, I don't know where to go from here.

---

### Post by Hugo74 on 2008-06-14
Hi editrix,

I think I solved my problem for the moment. Using strace to track the problem down I saw that it was always hanging with network timeouts. Trying to ping localhost I was really astonished that it timed out while the internet in general worked fine.

If you try a "ping localhost" and it doesn't work for you either take a look on your network settings with "ifconfig". If there is no loopback (lo) available than you really have the same problem.

With "sudo ifconfig lo 127.0.0.1" you can set up you loopback device at least temporary.

hugo74

---

### Post by editrix on 2008-06-15
> **Hugo74 said:**
> 
If you try a "ping localhost" and it doesn't work for you either ...

It worked fine, but thanks. I'm beginning to suspect my problem's got something to do with Gnome somehow conflicting with KDE. I've got the Gnome wheel spinning instead of KDE's watch when something loads, and a few other Gnome-y things I shouldn't be seeing. Sigh!

---

