---
title: "Installing Windows On Different Partition Of Same Disk With Ubuntu On?"
date: 2008-03-30
forum: General Help
---

### Post by minardips05 on 2008-03-30
Hi, for those of you that understood my title, i need help installing windows onto the same hard  drive, but a different partition. I have created a new partition in NTFS format using gparted, which is around 20 gigs, i have another section for Ubuntu still. Now what i am struggling with is when i try to boot from my XP CD when my computer starts, it will load the CD for a few minutes, then stop loading the CD and show me something similar to the blue screen of death lol. The CD shows up in Ubuntu and will open, but when i click, "install XP" ti will go to the first screen then become idle. I don't know how long i need to wait for the CD to load but i have waited a few minutes but nothing has happened. It maybe the CD, as it is a little scratched, but it will load in both scenarios but then do nothing.

I need windows for various applications such as Zune, iTunes for iPhone, PSP sync, Xbox file share system and various work. I had XP on my system before, before upgrading to vista, and then finally changing to Ubuntu.

I have tryed using VMware but it wouldnt install.

I have a Dell Inspirion 1300, 1.5gb of RAM, 40GB HDD. 

If anyone out there can help, it would be greatly appreciated.

Thanks, James.

---

### Post by forestpixie on 2008-03-30
Is it a primary partition or a logical partition that you have for win ? If you're not sure post

```
sudo fdisk -l
```

---

### Post by strabes on 2008-03-30
[http://ubuntuforums.org/showthread.php?t=358183](http://ubuntuforums.org/showthread.php?t=358183)

Also see the grub link in my signature.

---

### Post by minardips05 on 2008-03-30
I Think it is a primary section as i set it as a bigger section as windows seems to fill up faster, is there a way to easily check?

---

### Post by forestpixie on 2008-03-30
If you run the command I gave it will tell us if it's primary or logical, but if you can't remember making it a logical inside an extended I'd assume it's a primary. 

It might be that the partition needs to be at the front of the drive ofr win to see it - not sure about xp or vista requirements.

Primary and logical aren't actually anything to do with how big they are.

---

### Post by minardips05 on 2008-03-30
Ok so this is what i got.

  Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2167    17406396   83  Linux
/dev/sda2            4660        4864     1646662+   5  Extended
/dev/sda3            2168        4659    20016990    7  HPFS/NTFS
/dev/sda5            4660        4864     1646631   82  Linux swap / Solaris



so if the NTFS is thrid on the list, i'd assume it currently a logical partition, and not primary, and also that its not at the front end of the disk. Could i Move it to the front end and make it a primary partition with gparted?

---

### Post by minardips05 on 2008-03-30
Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2167    17406396   83  Linux
/dev/sda2            4660        4864     1646662+   5  Extended
/dev/sda3            2168        4659    20016990    7  HPFS/NTFS
/dev/sda5            4660        4864     1646631   82  Linux swap / Solaris

Partition table entries are not in disk order


I just re-read it and noticed this bit, anyhow, the NTFS volume isnt at the front end, that so sure, but im unsure about the rest. ^^

---

### Post by forestpixie on 2008-03-30
Open gparted and see what it looks like - but it's not in the extended - perhaps it need to be at the front. It can take some time to do.

I would say though that it could be the cd - if it starts and then fails it's not getting as far as the partitioning part of the install.

---

### Post by minardips05 on 2008-03-30
OK thanks mate, ill have a go at that tomorrow as i have to go now, and ill get back to this thread if that doesnt work.

Many thanks. James

---

