---
title: "[SOLVED] mkswap"
date: 2007-06-08
forum: General Help
---

### Post by celticbhoy on 2007-06-08
I have put a swap file on my vista drive by accident, using mkswap command. What command do I use to reverse the procedure ???

---

### Post by yabbadabbadont on 2007-06-08
What exactly was the command you ran?

---

### Post by celticbhoy on 2007-06-08
"mkswap /dev/sda1"

---

### Post by yabbadabbadont on 2007-06-08
Your Vista installation is now gone....  :(

Always tripple check commands before running them.  ;)

---

### Post by celticbhoy on 2007-06-08
No its is still there, but I have to boot in through my recovery partition. The problem is that without removing the swap file I cant set about fixing the boot.

---

### Post by yabbadabbadont on 2007-06-08
You need to read the mkswap manpage.  You didn't create a "swapfile", you initialized the whole vista partition for swap space.  Luckily, it appears that it just destroyed the boot files that vista uses and not the whole thing.  Not sure how you can recover from that unless the vista recovery mode can restore it's boot files.

---

### Post by celticbhoy on 2007-06-08
I am guessing that the only reason there is not more damage to the Vista drive is that the PC has 1G of ram, and Ubuntu has not had much reason to use it. I also realised the error I had made before turning the swap ON. All I really want to know is if there is an oposite command to "mkswap". I had a look with "man mkswap" but there does not seem to be a referance to any removal, or way to un-tag the drive.

---

### Post by Mr. C. on 2007-06-08
There is no undo for the mkswap command.  If any (important) part of that partition has been written, consider the data on it to be suspect.

You may be able to simply change the partition type back to NTFS.  Use parted or gparted to change the partition type to see if that might salvage the partition.

MrC

---

### Post by celticbhoy on 2007-06-08
Already tried that, the only option I got from Gparted, was to swapoff, but as the swap was never turned on it says it cant de-activate swap, and invalid argument.

I realise that this down to my own lack of care, but there must be some way to reverse this.

---

### Post by celticbhoy on 2007-06-08
If I use "mkfs" in parted on the drive, will it wipe the contents ???

---

### Post by yabbadabbadont on 2007-06-08
Yes.  That is the same as format in DOS/Windows.

---

### Post by yabbadabbadont on 2007-06-08
You previously stated that you could get into Vista using a recovery partition.  You will need to use the recovery tools provided by Vista to fix this.  (if it is even possible)

---

### Post by celticbhoy on 2007-06-08
I thought that might be the way so I try'd using one of the 'tools'on the Vista recovery partition to reset the boot/startup. It was one of those automatic jobs, and after it was finished, it boots into Vista through the recovery partition, and then runs normally. All the apps on the recovery partition are still there, but I dont know if any will change the reported file system, and remove any info 'mkswap' may have written.

Going to sleep on it for the night to see if I can get any ideas with a clear head in the morning.

Any ideas welcome, and if anything works I will post any results.

Thnx in advance to anyone who has given this any thought.

---

### Post by Mr. C. on 2007-06-08
Use fdisk then.

fdisk /dev/sda

type** l** (letter ell) to see the list of file types, **p** will print out the partition table, **t** to change the partition type, and then select the partition number.  Change the type to 7 and then **w** to write.

MrC

---

### Post by celticbhoy on 2007-06-09
Before I jump in head first, will using fdisk clear or preserve the files on the drive ????

---

### Post by celticbhoy on 2007-06-09
fdisk replies with

Unable to open /dev/sda

Yet, sda, sda1 & sda2 are all listed in /dev

---

### Post by celticbhoy on 2007-06-09
OOOOPPPSS, forgot sudo

---

### Post by celticbhoy on 2007-06-09
OK now I am really confused, fdisk shows the partition as NTFS, which it should be, but there is no * under the boot heading. Does that mean is I can restore the Vista boot info to the disk it should work ok ?????

---

### Post by Mr. C. on 2007-06-09
It is best to show your actual commands and output, as they appear on the terminal rather than posting your interpretation.  Too much important info is lost.

fdisk will not touch the file system when you change the file system type; it alters only the partition map.

Show the output of :

```
sudo fdisk -l /dev/sda
```

MrC

---

### Post by celticbhoy on 2007-06-10
Output below :-


Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            3499       30401   216098347+   7  HPFS/NTFS
/dev/sda2   *           1        3498    28097653+   7  HPFS/NTFS

Partition table entries are not in disk order


But gparted lists the drive as a swap drive !!!

---

### Post by sibun on 2007-10-05
I've done virtually the exact same thing!

Dual booting Ubuntu and XP
Using ntfs-config to view XP partitions under Ubuntu
Did accidental mkswap on an XP partition

XP boots and works fine, and recognises the partition still as NTFS but Ubuntu and GParted see it as linux swap!  If I could find out which files actually get changed with mkswap I could possibly replace them from an old backup.

Celticbhoy - did you have any success?

---

### Post by celticbhoy on 2007-10-05
No.
 The PC still works OK, but I am booting into Vista through my recovery partition. I guess it will do until something goes pear shaped, and then I will suffer.

---

### Post by sibun on 2007-10-08
This post by mar_rud from a similar thread might help :-
[http://ubuntuforums.org/showpost.php?p=3492728&postcount=16](http://ubuntuforums.org/showpost.php?p=3492728&postcount=16)

---

### Post by celticbhoy on 2007-10-10
Thanx that post worked well. If anybody has the same problem I can recomend the link above.

---

### Post by aot2002 on 2008-02-03
also for anyone using vista you can do a recovery by booting vista DVD and then choose repair computer and choose auto repair which will detect the boot sector and repair it

hence reversing and reinstalling the vista mbr

---

