---
title: "Changing a Hd File System"
date: 2006-11-09
forum: General Help
---

### Post by llanitedave on 2006-11-09
I have a 160G second hard drive on my Edgy AMD64 desktop.  I use it mostly for photos and backups, including from my wife's computer.

When I installed it, I was using SuSE 9.3, and I've since converted to Kubuntu.  The drive was formatted for the Reiser fs, but ever since I installed Edgy, whenever I boot it complains that the DMA is turned off, and it has to do a complete fs check, and it takes a long time.

I think I'd be more comfortable if the drive was formated into ext3 like my primary drive, but if that requires a reformat and offloading and then reloading tons of data, it may not be worth it.

Is there a way to change file systems without reformatting and deleting?  Or is it a pipe dream?

Would it cause trouble to turn on the DMA -- that's something I really an unfamiliar with.

---

### Post by johnnymac on 2006-11-09
I don't think your gonna find a way to lay down a new file system without loosing your data.

---

### Post by BLTicklemonster on 2006-11-09
Did you format edgy in Reiser fs? I did, and it's incredibly faster than ext3, in my opinion. I wonder if you had, if it would still have problems?

---

### Post by kerry_s on 2006-11-09
you can try adding " dma " to your boot line in /boot/grub/menu.lst

kernel		/boot/vmlinuz-2.6.17-10-386 root=/dev/hdd3 ro quiet mem=1000M vga=normal dma

---

### Post by llanitedave on 2006-11-09
Thanks all, for the quick replies.  I'll resign myself to keeping my second hd a reiser.  Not really a big deal.  

kerry_s, I'm tempted to follow your advice, but I need a clarification.  When I specify "vga = normal dma" is that going to set the dma on my boot drive, or all drives?  It's not my boot drive that's giving me the message, (hdc1), it's my second drive.(hdd2)

I just want to make sure I don't cause another problem elsewhere!

---

### Post by kerry_s on 2006-11-10
> **llanitedave said:**
> Thanks all, for the quick replies.  I'll resign myself to keeping my second hd a reiser.  Not really a big deal.  

kerry_s, I'm tempted to follow your advice, but I need a clarification.  When I specify "vga = normal dma" is that going to set the dma on my boot drive, or all drives?  It's not my boot drive that's giving me the message, (hdc1), it's my second drive.(hdd2)

I just want to make sure I don't cause another problem elsewhere!


Not "vga = normal dma" you just need the " dma " part, i just copied the line in mine, vga is a extra setting i use for my setup.

Adding dma will turn on dma for all drives. It should not cause a problem your just turning on a setting that is already there but off. It might also be you have a old drive that does not support dma, not likely, but possiable.

---

