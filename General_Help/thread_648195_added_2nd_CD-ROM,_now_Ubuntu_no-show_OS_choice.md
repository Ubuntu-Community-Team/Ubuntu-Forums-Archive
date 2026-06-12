---
title: "added 2nd CD-ROM, now Ubuntu no-show OS choice"
date: 2007-12-23
forum: General Help
---

### Post by riohondo on 2007-12-23
I run a dual-boot with XP and Gutsy. Yesterday I added a 2nd optical drive. This went into a microATX case, and it's layout prevented me from keeping my hd/cd1 on the same ide channel. Because I didn't have an IDE cable long enough, I had to put both optical drives on IDE channel 1, and my Ubuntu sysem as it's own master on IDE channel 2. 

The XP volume is on a SATA drive, no trouble there. 

Anyway, after switching my Ubuntu hard drive from IDE 1, to IDE 2, it's system no longer is recognized as a bootable OS. Only XP is shown as a choice. I tried  reversing IDE ribbons, with no change. I haven't yet  returned everything to its original assignment because I'd really love to have two optical drives. 

I've tried altering the BIOS so that SATA channel is shut down, but Ubuntu is still AWOL as a bootable choice.  It is recognized in the BIOS correctly, but is no longer blessed on startup. 

What am I missing?  Thank you.

---

### Post by skat3h3ll on 2007-12-24
i am still new at ubuntu and linux but it sounds to me that grub is now confused as to where the ubuntu partition is located, try running your live cd and changing grub settings. i dont know what to suggest other than this since i am new at everything still, heck i dont even know how to edit grub settings. but i do know that it is possible and i assume its possible from your ubuntu live cd 

sorry i am not of anymore help than this.

---

### Post by riohondo on 2008-01-01
That did the trick. Thank you for reminding me about the Live CD.  I was about to reformat my whole partition and start over. I sent off for the CD, because the one I downloaded took quite a long time to boot the machine. I don't know if that's normal, so I am going for the pre-made disc. Thank you very much!

---

