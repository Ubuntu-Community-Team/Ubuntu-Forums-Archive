---
title: "Citrix client 9, kubuntu 6.10, no minimize/maximize/close buttons on remote apps"
date: 2007-03-28
forum: General Help
---

### Post by apundir on 2007-03-28
Hi,
I have installed citrix 9.0 client on my freshly installed Kubuntu 6.10 laptop (Dell D820). The problem is that after launching the remote applications (which are windows applications like IE, putty etc), I am not able to see menu items on apps, also minimize/maximize/close buttons on application title bar are blank squares. I can't see typed characters in IE pages, I can see typed characters only after selecting them with mouse. Many more problems like these.

So fare I have installed following
- libxaw7, libmotif3, libxt6, firefox, mozilla

citrix plugin is working fine in firefox (after I added "LD_PRELOAD=libXt.so.6" in firefox rc) as I can see it in about:plugins as well as applications are launched automatically from firefox.

I have even tried tweaking windows settings from Tools->Settings using wfcmgr without luck.

I have also tried launching this app using wfica.sh CLI (after saving it to local hard disk) to see any additional problem, no luck here as well.

I have also symlinked /usr/lib/libXaw.so.6 -> /usr/lib/libXaw7.so.7.0.0 (as I could see it from one post)

I have also tried installing citrix client 10.0 without any luck, it crashes very often on my system, citrix 9.0 is stable at least in this regard.

Any pointers in debugging this problem further are very much appreciated, I have banged my head ](*,) in all the directions I could think of (or could find on net searches).

Thanks,
Avnish

---

