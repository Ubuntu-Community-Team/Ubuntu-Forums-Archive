---
title: "cloning 100GB to 200GB - root not visible/bootable"
date: 2008-02-18
forum: General Help
---

### Post by gomoku77 on 2008-02-18
Good morning all.

I am a new Linux user.  I have a 100GB drive in my Lenovo laptop.  On it I have managed to set up dual-boot (GRUB) with Win XP (60GB) and Ubuntu 7.10 (40GB) -- to which I upgraded from 7.04 a couple of days ago. 

I want more space.  I bought an external 200GB 2.5" USB 7200 RPM portable drive, which I eventually intend to swap for my current internal 5400 RPM 100GB drive.  I downloaded a free (full) trial version of Acronis TrueImage to clone the 100GB disk to the new, larger one.

I had the option of cloning "automatically", which would apparently require me to remove the "old drive" as the last upgrade step, something I didn't want to have to do until 100% sure the upgrade had gone well. So, I went "manual", sizing my own partitions on the new USB drive (/ 8G, /boot 1G, /tmp 8G, /var 8G, /usr 8G, and /home 50G approximately,  in addition to the NTFS area for XP (90G).  

No problem there, except for one thing.  The issue:  how to make the root "/" partition visible and bootable on the new disk. I have read up a bit on this, and looked into getting Supergrub, a shareware tweak tool. Before I go off overcomplicating things due to my ignorance, my question to you is:   "is there a SIMPLE  way of fixing this problem on the new USB drive, perhaps while booted into Ubuntu on my current "old drive" (still there, working fine)?

This is probably trivial to some.  Or many.

Thanks in advance.


Regards,
gomoku

---

