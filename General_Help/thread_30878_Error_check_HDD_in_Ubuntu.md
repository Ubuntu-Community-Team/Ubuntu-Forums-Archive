---
title: "Error check HDD in Ubuntu"
date: 2005-04-30
forum: General Help
---

### Post by DutchLau on 2005-04-30
Hello Ubuntu community,

Does anyone have a solution for me? I have a massive problem. I have and external HDD that I put inside my computer (ATA) and I'm trying to copy the files from my external (hdb - fat32) to my master drive (hda - ext) so that I can reformat hdb to ext 3 or 2. Okay, this *shouldn't* be a problem, yet it is. While copying the 7000 odd backup files (don't ask me what they are) with Nautilus (good old simple ctrl-c and ctrl-v), it stops in the middle of the copying and the system hangs and becomes unresponsive. When I do this with a Ctrl-Alt-F2 console I also get the same problem but it shows me something like "cylinder fault on bla,bla,bla..." so my suspicions tell me that there are errors on the HDD somewhere. 

Now the question is: how can I run an error check with Ubuntu for my fat32 HDD and correct those errors so that I can copy the files and reformat that HDD afterwards?

Basically, how can I run an error check on my HDD and correct those errors. 

Thanks already,

DutchLau

---

### Post by emuman on 2005-04-30
You can check it with "sudo fsck.-t vfat /dev/hdbX" where X is your partition number. Try a "sudo fdisk /dev/hdb" and then "p" for printing the partition number on the external hard drive.

---

### Post by DutchLau on 2005-04-30
Hi and thanks for your speedy reply,

This is what I'm getting at first. What should I do?

There are differences between boot sector and its backup.
Differences: (offset:original/backup)
  65:03/00, 71:20/00, 72:20/00, 73:20/00, 74:20/00, 75:20/00, 76:20/00
  , 77:20/00, 78:20/00, 79:20/00, 80:20/00, 81:20/00
1) Copy original to backup
2) Copy backup to original
3) No action

I don't quite understand what's happening. 

Cheers,

DutchLau

---

### Post by emuman on 2005-05-01
Choose 1) to synchronize the backup and boot sector or 3) do ignore this.

---

### Post by DutchLau on 2005-05-01
Hi again, I just did what you said. This is the log I received from the disk-check:

>  dosfsck 2.11, 12 Mar 2005, FAT32, LFN
There are differences between boot sector and its backup.
Differences: (offset: original/backup)
  65:03/00, 71:20/00, 72:20/00, 73:20/00, 74:20/00, 75:20/00, 76:20/00
  , 77:20/00, 78:20/00, 79:20/00, 80:20/00, 81:20/00
1) Copy original to backup
2) Copy backup to original
3) No action
? 1
Free cluster summary wrong (2445709 vs. really 2307003)
1) Correct
2) Don't correct
? 1
Leaving file system unchanged.
/dev/hdb5: 17123 files, 2575312/4882315 clusters


I already changed the ownership of the HDD to me, but but still nothing will happen. It's as if it won't do anything. It's a 160 GB HDD which is about 50% full. (It's hdb5 but hdb2 is the extension or something) and the error check is done in about 20 seconds - impossible! 

EDIT: Everytime I redo the disk-check it still tells me that the "free cluster summary is wrong" even though I ask to correct it. 

Anyone else have any suggestions?

DutchLau

---

### Post by emuman on 2005-05-02
If SMART ist enabled you can show the drive health status with 

smartctl -H /dev/hda

See 
[HOWTO Monitor your hard disk(s) with smartmontools](http://gentoo-wiki.com/HOWTO_Monitor_your_hard_disk(s)_with_smartmontoolstest)

---

