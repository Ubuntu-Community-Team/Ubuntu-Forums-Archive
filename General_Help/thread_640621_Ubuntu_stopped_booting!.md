---
title: "Ubuntu stopped booting!"
date: 2007-12-14
forum: General Help
---

### Post by Zophixan on 2007-12-14
Hey guys, I'm new to linux so I'm a bit clueless at the moment. Ubuntu was working fine till today when it wouldn't boot up. It just goes to a screen where there is a flashing line - where you can type but it is not a bash command line. I've tried recovery mode where I can access bash - from there I unmounted the partition and ran fsck but no problems were found. I tried to run from recovery, aquamarine , but it claims that it can['t init the x server or something? Any ideas guys?

---

### Post by Joshua on 2007-12-14
I'm not sure I understand exactly what you are describing.  Have you watched it try to boot from the command line?  What kinds of messages do you get?

Have you updated recently, ie. installed all the updates with the update manager?

One problem I've had is with the nvidia graphics card drivers.  When I used to update the kernel, sometimes the drivers wouldn't be updated for several more days or weeks.  So the next time I tried to boot, it would throw several errors about an improperly configured driver and inability to start the x-server.

---

### Post by Zophixan on 2007-12-14
Hi, basically it boots up to the black screen with the possibility to type (but no commands, letters come up though). Thats all I can say really - in recovery mode, I can get to a bash prompt - I noticed that it said swap disc fail or something earlier though?

---

### Post by Joshua on 2007-12-15
I'm sort of at a loss, but when you boot in recovery mode can you type:
```
fdisk -l
```
and post the results here.

It may say if your swap partition is recognized or not... I'm not an expert or anything, but I'm not sure if a swap partition is even needed until you start using up all your RAM, though.  So I don't know if a bad swap partition would prevent you from booting.  Maybe someone else can answer that.

The command dmesg (diagnostic message) executed after boot should print the kernel message buffer.  <page up>, or maybe <shift>+<page up> should allow you to scroll up the terminal screen to review the messages that were posted.  Then you can find exactly what the error message was.

---

