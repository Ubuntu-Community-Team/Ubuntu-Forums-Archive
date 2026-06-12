---
title: "Creating new partition, help needed."
date: 2006-12-22
forum: General Help
---

### Post by hoagie on 2006-12-22
Ok today windows for some really strange reason deleted its self partition (a whole 149Gb sata disk).
I decided since I don't need windows (I was just keeping it in case something went with ubuntu)
and since it deleted it's self, to format the hole disk, create one ext3  (or fat32 don't know what's best)partion that will be for storing files.(for ubuntu ofcourse) I want this partition to take the whole disk, all the 149GB.

Ok here's how my system disks are organized:

Hda (Ide) 80gb:
hdc1 ext3 (ubntu)
hdc5 swap memory (ubuntu)

Sda (SATA):
-



Thanks in advance

---

### Post by jeremy on 2006-12-22
You can install gparted from the repos. It is very easy to use.

---

### Post by dannyboy79 on 2006-12-22
> **hoagie said:**
> Ok today windows for some really strange reason deleted its self partition (a whole 149Gb sata disk).
I decided since I don't need windows (I was just keeping it in case something went with ubuntu)
and since it deleted it's self, to format the hole disk, create one ext3  (or fat32 don't know what's best)partion that will be for storing files.(for ubuntu ofcourse) I want this partition to take the whole disk, all the 149GB.

Ok here's how my system disks are organized:

Hda (Ide) 80gb:
hdc1 ext3 (ubntu)
hdc5 swap memory (ubuntu)

Sda (SATA):
-



Thanks in advance

wouldn't u want to learn why windows deleted it's own partition before you go ahead an move on??? if not then, just do what the other guy said, sudo aptitude install gparted. then simply run it from your pull down menu or from a terminal, gksudo gparted. if you were running dual boot, I am guessing that your entry in grub was simply deleted and not the entire partition. OS's don't just decide to delete the partition they reside on. was this a windows install on a completely different computer or a dual boot? i don't know why I am asking it's just that I would think you should figure this out first. I mean what if this drive isn't any good? then you start putting data on it and then your data ends up disappearing one day!! did you think about that?

---

### Post by hoagie on 2006-12-22
Tried gparted but after creating a partition, nothing happened ubuntu didn't recognized it, so I thought I did something wrong.

---

### Post by xopher on 2006-12-22
> **hoagie said:**
> Tried gparted but after creating a partition, nothing happened ubuntu didn't recognized it, so I thought I did something wrong.

Remembered to create a filesystem on the newly created partition too? Oh, and press apply in GParted? :)

Errare humanum est.

---

### Post by hoagie on 2006-12-22
> **dannyboy79 said:**
> wouldn't u want to learn why windows deleted it's own partition before you go ahead an move on??? if not then, just do what the other guy said, sudo aptitude install gparted. then simply run it from your pull down menu or from a terminal, gksudo gparted. if you were running dual boot, I am guessing that your entry in grub was simply deleted and not the entire partition. OS's don't just decide to delete the partition they reside on. was this a windows install on a completely different computer or a dual boot? i don't know why I am asking it's just that I would think you should figure this out first. I mean what if this drive isn't any good? then you start putting data on it and then your data ends up disappearing one day!! did you think about that?

I'm curius about finding that out too. Windows was dual booting with ubuntu on 2 different hard disks. I don't think that the disk has a problem, it worked fine up till today and I don't really know what happened while I was using ubuntu, but somehow windows...deleted it's own partition. 
First I though it was grub's problem, so I changed the disk priority to the windows one but I still got the same.

---

### Post by hoagie on 2006-12-22
Ok I edited fstab and everything is fine now. Great thank you people.

---

