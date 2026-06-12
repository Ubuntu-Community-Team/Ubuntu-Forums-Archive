---
title: "Adding a FAT16 OS to Grub - NTLDR error"
date: 2007-08-16
forum: General Help
---

### Post by hurtstotalktoyou on 2007-08-16
Hey, all.

So, I have a primary hard disk which I have divided into three partitions, one for Windows XP, the second for Ubuntu, and the third, of course, as swap.  This was the state of things when I installed Ubuntu on top of Windows, and the Grub Bootloader managed everything just fine.

Now, when I installed Ubuntu (and Grub), I also had a second disk, which at the time had Freedos installed on it.  Grub successfully detected Freedos, and it booted fine.  However, I didn't much care for Freedos, so I reformatted the second disk and installed MS-DOS 6.22 instead.

Now it doesn't work.

I've played with the menu, adding (hd1,1) and (hd1,2) to the original (hd1,0), which had been Freedos.  Nothing works.

This is the error I get:

**BOOT:  Couldn't find NTLDR**

Yet, if I bypass grub and choose my motherboard's boot device selection, DOS loads just fine.  So it's got to be a Grub issue.

---

### Post by bodhi.zazen on 2007-08-16
NTLDR : [http://tinyempire.com/notes/ntldrismissing.htm](http://tinyempire.com/notes/ntldrismissing.htm)

Error 12 : [http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#12_](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#12_)

---

### Post by hurtstotalktoyou on 2007-08-16
> **bodhi.zazen said:**
> NTLDR : [http://tinyempire.com/notes/ntldrismissing.htm](http://tinyempire.com/notes/ntldrismissing.htm)

Error 12 : [http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#12_](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#12_)

Thanks for the advice.  The error 12 thing might have worked, but it turns out the problem on that partition was with Windows NT, not Grub.  So I just deleted and reformated the partition altogether; maybe I'll install Damn Small or something in its place.  As for the NTLDR link, that seems to be about problems booting into DOS apart from Grub, but, as I have edited my OP to show, I can boot into DOS just fine using my motherboard boot device selection.  I just can't boot into it from Grub.  But I thank you for the effort.

---

### Post by hurtstotalktoyou on 2007-08-17
bump for help

---

### Post by hurtstotalktoyou on 2007-08-18
bump for help

---

