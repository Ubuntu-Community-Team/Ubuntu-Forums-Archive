---
title: "Cannot Mount Drive"
date: 2006-12-06
forum: General Help
---

### Post by Scheater5 on 2006-12-06
After I gave up on [getting Beryl to work]("http://ubuntuforums.org/showthread.php?p=1854017") on my Kubuntu install (and just really wanting a nice clean desktop anyway) I created another partition and made a clean install.  Works great - lovin' Beryl.  But now Grub doesn't recognize the other installs (which I figured it wouldn't) but the trippy thing is I can't mount it (QTParted identifies it as sda1).  I can't find it!  Nothing under /media.  "locate: sda" in Konqueror yields nothing.  Using QTParted to make sda1 Active seemingly does nothing.  I'm lost - being able to switch between the partitions would be idea, but if I can even just mount it to salvage some files I'll be happy.  I intend on scrapping the install anyway once I get the new partition set up right.  Anyone have any ideas?

---

### Post by Scheater5 on 2006-12-07
Well, I never did figure out how to mount the drive, but I can switch back and forth between the partitions now - albeit through a rather arduous process.  I rewrote Grub to hd0,0 and my old installation booted like a champ.  So, now I just have to move grub every time I want to go from my "play" partition to my "work" partition - I think the next chance I have alot of freetime I'm gonna back everything up and make a seperate partition for /home so I can do this kind of experimenting more easily.  If anyone knows how to get grub to recognize both partitions I'd love an easier solution.  Thanks guys.

---

### Post by Scheater5 on 2006-12-07
Alright, back in my "work" partition, I load up QTParted, and it identifies my "play" partition as sda2

```
sudo mount /dev/sda2
```
yields

wrong fs type, bad option, bad superblock on /dev/sda2,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

Now, it would seem to solve the whole problem (until I reformat and make a seperate /home partition) if I could do this from the "play" partition.  If I could simply access the files from that partition I would have a all of my files and still be able to "play" in relative safety - so what's this error about fs type?

---

### Post by Scheater5 on 2006-12-08
Stick a fork in this one - it's done!

Found what I needed on governmentsecurity.org - [here]("http://www.governmentsecurity.org/archive/t14366.html").  

The instructions on the site said 
```
cd /mnt/
mkdir drived
mount /dev/hda5 /mnt/drived
```
So I just modified the filenames to sda1 and "work" instead of hda5 and drived.  

Problem resolved

---

