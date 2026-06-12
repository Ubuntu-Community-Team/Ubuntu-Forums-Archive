---
title: "Deleted grub on accident :("
date: 2008-01-23
forum: General Help
---

### Post by Palombax on 2008-01-23
I deleted grub partition today on accident, now i cant boot into windows or anything at all, Is there a fix? im posting on my ancient desktop, 

I was trying to clear space and couldent see a use to the partiion and now i cant use my laptop! i need it back up as quick as possible

thanks guys! 


Palombax

---

### Post by HermanAB on 2008-01-23
The easiest way to fix a mess like that is to re-install.  It only takes about 30 minutes, if you have a separate /home partition - just don't format /home.  If not, then you now know why you should have a separate /home partition and then you have to backup /home first using your live CD.

Cheers,

Herman

---

### Post by Palombax on 2008-01-23
cd wont load, i just get error 17 in grub, Xp ran fine when i did the partition deletes, just when i restarted it wont boot, Livecd wont run either, i have my cd drive set to boot first

---

### Post by aldenhg on 2008-01-23
See if your BIOS has a boot order option. On my desktop if I hit F8 I get a list of the bootable devices. The boot order isn't always what it should be. If you can get it to boot off a CD I'd reccomend booting the LiveCD and reinstalling Grub. It's not too tough, though it does involve a bit of work at the command line. The instructions [here]("http://www.arsgeek.com/?p=655") are for an older version of Ubuntu, but grub hasn't changed since then. Just make sure that you know where all your stuff is located (what I mean should be obvious after reading the link) before you do anything potentially destructive.

---

### Post by Palombax on 2008-01-23
ive done that, still wont do it, cd loads fine on this desktop, my bootorder is cd then my harddrive

---

### Post by capink on 2008-01-23
If you have the windows cd you can resotre your mbr following this [guide]("http://amazingrando.wordpress.com/2007/04/05/fixmbr-is-your-friend/").

If you don't have the windows cd I heard that [super grub disk]("http://supergrub.forjamari.linex.org/") is able also to resotre windows bootloader.

---

### Post by Palombax on 2008-01-23
ive made a working supergrub cd, tried my live cd, and windows, my cd rom is set to boot first, but still wont load off the cd's it like, passes it and goes stright to grub

---

### Post by aldenhg on 2008-01-23
It sounds like your MB or CD drive might be a bit fubar. Try forcing the motherboard to reset by unplugging the computer, taking out the CMOS battery, holding the power button for 30 seconds and then putting it all back together and trying again. If that doesn't work, see if you can't scare up another CD drive to test with.

---

