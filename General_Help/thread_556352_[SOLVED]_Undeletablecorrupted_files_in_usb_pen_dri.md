---
title: "[SOLVED] Undeletable/corrupted files in usb pen drive. HELP :(!"
date: 2007-09-21
forum: General Help
---

### Post by musafirah on 2007-09-21
I have a USB flash drive and it will no longer allow me to add files to it and there are a bunch of 'ghost' files that I thought I had deleted but they take up space and are simply unknown types. I can't get rid of them. there are also not in the .Trash-user folder that nautilus created in the drive (which i also cannot rid myself of), they show up as unknown files.  i have tried changing ownership and it just keeps coming up as "read-only file system."  i think it perhaps has something to do with me mistakenly thinking the files had deleted when i hit delete and did not unmount the device properly (?)

can someone please help me? i just want to get rid of these files  and be able to use my usb stick normally! if it means completely reformatting it and/or getting rid of everything on it i don't care, i just want to use it again.. just tell me exactly how (kind of a newbie)

Thank you


(ps.  i'm running on edgy eft)

---

### Post by ddrichardson on 2007-09-21
Is there stuff on the drive you need to keep? If so then copy it then fdisk the thing.

---

### Post by tszanon on 2007-09-21
I've seen something like this before. I formatted my mp3 player as fat16 using gparted. Somehow, it was being recognized as 2 partitions, 256 MB each (it has 256MB of memory). Windows only recognized one of the partitions, the mp3 player only recgnized the other partition, and Ubuntu recognized "both". In Windows, there were some files with strange (and impossible for a windows system) names. I couldn't delete those files. The funny thing is that those files allocated a total of 4 GB, 16 times its capacity. :)

I had to go back to gparted and delete the only partition it showed me. Now everything works fine. i just don't know how it works, since there's no partition there.

---

### Post by ddrichardson on 2007-09-21
Fat 16 has some serious limitations such as the number of files in a directory needs to be less than 256.

---

### Post by tszanon on 2007-09-21
> **ddrichardson said:**
> Fat 16 has some serious limitations such as the number of files in a directory needs to be less than 256.
I chose it because it was the filesystem type used before. And I had to choose something that:
1. I could use at work (windows);
2. I could use in ubuntu (I don't use ntfs-3g, so NTFS would not be an option)
3. the mp3 player firmware supported.

Actually, I first tried FAT32, but I had the same problems. Since I use it mostly to store mp3 files, I probably won't face any problems regarding the limitations of FAT16.

I'm stopping now, I don't want to hijack the thread. :)

Thanks!

---

### Post by musafirah on 2007-09-23
this is the info on the device when i did fdisk -l

Disk /dev/sda: 4294 MB, 4294967808 bytes
255 heads, 63 sectors/track, 522 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         522     4192933+   b  W95 FAT32


can you please tell me what to do next to basically clean it out and start over?

---

### Post by ddrichardson on 2007-09-23
Well, you could just format it. You can do that from the desktop.

---

### Post by musafirah on 2007-09-23
thanks, but i really don't understand what to do.. HOW do i format it? also, the partition is locked and i can't do anything in gparted.

---

### Post by ddrichardson on 2007-09-23
Do it from a terminal to format it:```
sudo mkfs.vfat  /dev/sda1
```
If it still plays up do```
sudo  fdisk /dev/sda1
```
Delete the partition (d), create a new (n) one, select primary (p), choose the defaults and then format it.

If you still have problems then, chances are the flash disk is on its way to silicon heaven.

That said though I am wondering wether you have done something to the drive as sudo and are simply unable to delete because of a permission problem, if from the terminal you do```
ls -l  /dev/sda1
```Are the files listed as owned by root or a user other than you?

---

### Post by strabes on 2007-09-23
You can also try the command I wrote in the last section of [this](http://ubuntuforums.org/showthread.php?t=478901) thread which is similar to what ddrichardson told you to do.

---

### Post by musafirah on 2007-09-23
> **ddrichardson said:**
> Do it from a terminal to format it:```
sudo mkfs.vfat  /dev/sda1
```
If it still plays up do```
sudo  fdisk /dev/sda1
```
Delete the partition (d), create a new (n) one, select primary (p), choose the defaults and then format it.

If you still have problems then, chances are the flash disk is on its way to silicon heaven.

That said though I am wondering wether you have done something to the drive as sudo and are simply unable to delete because of a permission problem, if from the terminal you do```
ls -l  /dev/sda1
```Are the files listed as owned by root or a user other than you?

the files were listed as owned by root.. but sudo chown changed it to say owned by me. and it looks like mkfs.vfat works! so far so good..so thank you.
but, i did notice in the folder properties it says only I (user) can change and delete files. does that mean that when i plug in the drive on a different computer I won't be able to save and change things? should i do sudo chmod?
thank you

---

### Post by ddrichardson on 2007-09-23
No. Chances are that at some point you've used it as root, hence the undeletable files. You shouldn't have any problems now it's working.

---

### Post by musafirah on 2007-09-23
thanks! hopefully i won't have to post here again! (until the day i'm an expert telling other people how to fix their problems :)

---

### Post by ddrichardson on 2007-09-23
We all do from time to time, some of us even get lucky on answering! Can you mark the thread read - to aid others searching for your problem (There's a link in my sig)?

---

### Post by musafirah on 2007-09-23
ok, will do.. 
also there is one thing.. my problem started when i plugged the pendrive into my friend's computer which runs on windows.. and copied files from her computer. it copied some of the files but then it refused to copy more. i ran it as a root AFTER that happened. so i just want to make sure that if i plug it into Windows computers again i should ok with copying back and forth yes?

---

### Post by ddrichardson on 2007-09-23
Nope it wasn't windows - it was running as root.

---

