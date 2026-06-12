---
title: "turning an existing system into a dual boot"
date: 2008-06-13
forum: General Help
---

### Post by ktanner404 on 2008-06-13
Hello all,
    I'm just getting back into linux and am fairly rusty. (a few years back I was really into mandrake but fell off the wagon and started using windows again until just recently coming to my senses and downloading Ubuntu. I'm loving Ubuntu but have one issue;
I wasn't 100% sold after reading up on it but need to upgrade my HDD anyway. So I bought a new HDD took out the old one with xp on it, put in the new one and loaded Ubuntu up on it. The old HDD's been collecting dust for a couple months now, but my girlfriend still wants to use it for a couple things. So I pinned it as a slave and hooked it up. In the old days I set many a dual boots up by installing mandrake on a system with windows on it already but I have no idea how to do it with my systems set up separately as they currently are. So if anyone could help me, I imagine theres a way to set GRUB up again? I don't know, but thanks in advance!

---

### Post by forestpixie on 2008-06-13
You should be able to do it by adding to grub, this is the example

title		Windows 95/98/NT/2000
 root		(hd0,0)
 makeactive
 chainloader	+1

Try something like that to start with - obvioulsy get the right drive and partition number for the xp drive - I'd guess it's (hd1,0) if you only have 2 drives.

You might need the map command - but not sure as I never needed to use it myself.

---

### Post by trevelyan on 2008-06-13
also.. a quick fix while you figure out the proper way, is to get in the boot menu when the computer is booting up and selecting the hard disk with the operating system you want to use.

for example in my computer to do that, i reboot.. then when its autodetecting everything (ram, hard disks, CD-rom, etc.) i press F11 and i get a list of boot devices.

in your computer the F(#) key might be different. maybe F8. but it tells you in that screen. just look.

---

