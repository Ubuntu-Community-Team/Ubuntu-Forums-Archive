---
title: "Can't boot from hard drive"
date: 2006-12-28
forum: General Help
---

### Post by YoungCthulhu on 2006-12-28
I have just upgraded to Kubuntu 6.10 edgy.  Have done a full re-format of my HDD (old 20GB Quantum Fireball on an HP Pavillion 8630!).  Installation went OK, qparted could access the old partitions (previously had a small Windows 2000 ptn) and I opted for Kubuntu as the only OS on the machine.

It won't get past the blue Hewlett Packard start-up screen now but it will boot to the CD-ROM for Kubuntu installation.  Is there any way to get past this?  Is my boot script file corrupted or has my old HDD just "rolled up the curtain and gone to join the choir invisibule??" :confused: 

Any advice would be appreciated.
Cheers

---

### Post by Ex-XP on 2006-12-28
Did you completely blow away the old Windows partitions on setup?

---

### Post by Ex-XP on 2006-12-28
Another set of checks to make.....I'd re-verify the cable connection, BIOS settings, etc:  [http://ubuntuforums.org/showthread.php?t=321014&highlight=hp+bios](http://ubuntuforums.org/showthread.php?t=321014&highlight=hp+bios)

---

### Post by YoungCthulhu on 2006-12-28
Yes, it's all gone.  Message came up at an early stage of installation to the effect that it would "Create ext3 file system for / in partition #1 of IDE1"

Thanks for your reply
Cheers

---

### Post by taurus on 2006-12-28
[https://help.ubuntu.com/community/GrubHowto](https://help.ubuntu.com/community/GrubHowto)

---

### Post by YoungCthulhu on 2006-12-30
Thanks again Ex-XP, and thanks Taurus.  I downloaded the grub article and found it helped further my understanding of Linux.  Unfortunately my computer won't even get to the part where it loads the OS, and does not appear to even read it's BIOS, apart from sending an HP logo to the screen (???).  You should get a message to the effect that it's unpacking the Linux Kernel or something shouldn't you?  It doesn't seem to know it's a computer (perhaps it thinks it's a toaster?)

I heard somewhere about a CMOS battery on the motherboard.  The computer is about 8yrs old now, perhaps the battery has run down?  Or am I barking up the wrong tree? ](*,) 

Happy GNU year guys! :)

---

