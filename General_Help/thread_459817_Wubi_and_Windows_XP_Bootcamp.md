---
title: "Wubi and Windows XP Bootcamp"
date: 2007-05-31
forum: General Help
---

### Post by DaveP on 2007-05-31
From what I have read I should be able to install this onto my Windows XP Bootcamp setup on an iMac. Is this correct? Anyone have any experience of doing tis?

Great idea! Thanks to the developers of Wubi & Ubuntu.

---

### Post by Sam89364 on 2007-08-08
I have the exact same question!

I have a MacBook with windows installed under Bootcamp. Will I be able to use Wubi to install Ubunto on the WINDOWS partition of my MacBook?

This would be a perfect alternative for the complex triple boot procedure.

Sam

---

### Post by tuxcantfly on 2007-08-08
> From what I have read I should be able to install this onto my Windows XP Bootcamp setup on an iMac. Is this correct? Anyone have any experience of doing tis?

Yes, it should work. Then again, though, note that should you ever decide to remove Windows and switch back to Mac OSX, your Wubi install will be wiped out too. See LVPM and UNetbootin in my signature for how to avoid this problem by either upgrading your Wubi install, once you're installed using Wubi, or avoiding Wubi and installing directly to a dedicated partition (unlike standard Ubuntu, neither solution requires you to burn a CD). Of course, if you're just always going to keep Windows on your Mac, feel free to just install using Wubi without modifications.

---

### Post by tuxcantfly on 2007-08-08
Also, if you need additional general Ubuntu-on-mac tips (they'll work with Wubi and UNetbootin) see [https://help.ubuntu.com/community/MacBook](https://help.ubuntu.com/community/MacBook) and [https://wiki.ubuntu.com/iMacIntel](https://wiki.ubuntu.com/iMacIntel)

---

### Post by Sam89364 on 2007-08-08
Thanks tuxcantfly for the very prompt reply.

I was searching on the net for info in the issue. Unfortunately, the only person I could find who actually tried it seems to say that it won't work! (one of the comments on this page:
[http://www.downloadsquad.com/2007/05/10/wubi-makes-ubuntu-a-snap-for-windows-users/](http://www.downloadsquad.com/2007/05/10/wubi-makes-ubuntu-a-snap-for-windows-users/))

"It's a SHAME that this does not work with Apple BOOTCAMP. I've got Win XP installed with bootcamp and tried to install wubi... after reboot when choosing Ubuntu it can't locate the virtual disk image!!!!! WHAT A SHAME"

I am very tempted to trying it for myself. I was just wondering if you may have any thoughts regarding what that guy said.

---

### Post by tuxcantfly on 2007-08-08
> "It's a SHAME that this does not work with Apple BOOTCAMP. I've got Win XP installed with bootcamp and tried to install wubi... after reboot when choosing Ubuntu it can't locate the virtual disk image!!!!! WHAT A SHAME"

I am very tempted to trying it for myself. I was just wondering if you may have any thoughts regarding what that guy said.

Hmm come to think of it MacIntels have different partition tables than normal PCs do, maybe that screws up the Wubi hard drive autodetection code... In that case try doing a standard install instead, that should work (at least according to the people in the Intel-Mac Ubuntu subforum), if you don't want to use a CD for it just see UNetbootin at [http://lubi.sourceforge.net/unetbootin.html](http://lubi.sourceforge.net/unetbootin.html) and run that from your Windows install (use the windows .exe version, the one that says ubuntu704), it should work just as well as a standard Ubuntu install would, and you get the added bonus of Ubuntu not having any dependency on your Windows install (unlike Wubi).

---

### Post by ottozer0 on 2007-08-09
Sorry to say it...Ubuntu did not install on my mac....blah blah blah virtual thingy....hehe...So close to an easy setup...I this boot camp sure has is negatives sometimes...but at least I can still play my PC games on xp....Ubuntu one day you will be mine(install anyway):lolflag:

---

