---
title: "Can't boot anything"
date: 2007-03-27
forum: General Help
---

### Post by Martogh on 2007-03-27
Hi all, 

I had a machine with Kubuntu running on it fine until i (stupidly) wanted to be able to dual-boot windows xp too. The hard disk was already partioned with the first 15gb being ext3 and having kubuntu on it, and the next 64 gig being fat32 and used for storage, and the last 1gig being my swap partition.

I backed up everything on my fat32 partition, booted from windows xp disk and tried to install windows onto the fat32 partition. It said it couldnt install on that format, which I didn't understand cause it was fat 32. Anyway, I deleted the partition and tried to remake it. However it wouldnt let me pick any format on remaking this partition and it just said (raw) instead of fat32 or unknown (which is how it identified ext3). Unsurprisingly it still wouldnt let me install on this raw partition either. I later called my brother about this and he told me i'm best to install windows xp first, then linux on top of that if i want to dual boot, cause windows tends to stuff things up. As such I assume that windows xp wouldnt install because it didn't recognize the format of the other partitions. 

However my main problem is not installing windows, but is that after I've done all this my computer now won't boot to anything. It goes through BIOS and then sits there. My brother thinks it sounds like i have a problem with GRUB, and having done some reading on it that sounds like a reasonable hypothesis, although I dont understand why GRUB would be on the second storage partition and not the first O/S partition - i thought it was supposed to be on the first sector of the disk? In any case I really don't know how to fix whatever problem i've caused. I know i can just reformat it all and start from scratch, but i'd rather try to salvage it if possible (so i don't have to reconfigure everything, and can keep my old emails etc). I have a windows XP cd, and the Kubuntu 6.06 desktop CD, but i also have another PC next to this with which i can d/l anything else i may need. 

Thanks for your help :)

Matt.

---

### Post by zvacet on 2007-03-28
[http://ubuntuforums.org/showthread.php?t=358183&highlight=grub]("http://ubuntuforums.org/showthread.php?t=358183&highlight=grub")

---

### Post by Martogh on 2007-03-28
thanks was helpful, i see why ubuntu wouldn't load up, but i still dont understand why windows wouldnt install on my pc. Can windows XP not install on a fat32 partition? I had the partition fat32 cause I heard linux isnt good with ntfs, but after reading some threads today i've heard that has changed anyway...

---

