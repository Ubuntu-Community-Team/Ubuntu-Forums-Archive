---
title: "Resizing Drives"
date: 2006-08-18
forum: General Help
---

### Post by Doytch on 2006-08-18
On my main hard drive, I have my Windows XP NTFS partition, and my Ubuntu Ext3 partitions.  My data is on another hard drive using FAT32.

I want to resize my Windows partition, making it smaller and giving that extra space to Ubuntu. 

My plan was to use Paragon Partition Manager from inside Windows.  However, I wondered if this might cause any problems with either OS.  The only time I resized an OS partition was when I had only Windows on my disk and made it smaller.

GRUB is in the MBR, so is there any chance of screwing up either OS by doing this?

---

### Post by JerMe on 2006-08-18
There's always a potential for screwing things up when you mess with partitions.

With that said... GParted is what you're looking for.  GRUB doesn't regard partition size so there's no need to worry about GRUB getting confused (unless it looks for a partition that's no longer there.)

---

### Post by PriceChild on 2006-08-18
Just backup ALL your data that you couldn't bare to lose before doing anything.

As long as you do that, you can't really go too wrong.

---

### Post by Scythe!? on 2006-08-18
> **PriceChild said:**
> Just backup ALL your data that you couldn't bare to lose before doing anything.

As long as you do that, you can't really go too wrong.

Sorry to hijack the thread but if I delete my swap partition (hda2) (I have 1gb RAM and its never used) or reduce it to about 256mb, can I merge it with my ext3 ubuntu partition (hda3)

Will this mess up grub, or is it a matter of changing the menu.lst so it looks at hd0,2 when the 2 partitions are merged?

---

