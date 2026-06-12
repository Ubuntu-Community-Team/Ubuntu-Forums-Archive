---
title: "/wubi/linux error 17"
date: 2007-04-06
forum: General Help
---

### Post by Zsedcft on 2007-04-06
I installed wubi today, but when I select Ubuntu at the OS selection screen, it breaks at this line:
find --set-root /wubi/linux

and gives me error 17 cannot find file.

I checked the menu.lst file and everything matches up with the actual files.  How would I go about fixing this?

---

### Post by myoldryn on 2007-04-06
Do you tried to defragment your hard drive...
Error 17 means in most times, that the grub didn't find the kernel... kernel have to be in one piece..
Windows have this habit, to make hdd look like swiss cheese ... free space holes everywhere

---

### Post by ecology2007 on 2007-04-06
This is a known issue with grub, we are working on fixing it. It happens when the bootloader does not find the hard disk were wubi folder is. Try to move the wubi folder on your 1st partition.

---

### Post by Zsedcft on 2007-04-06
Do you mean move it to a different location on the first partition or move it from one partition to the first partition?  I only have one partition.  Would RAID settings effect this at all?

---

### Post by ecology2007 on 2007-04-06
> **Zsedcft said:**
> Do you mean move it to a different location on the first partition or move it from one partition to the first partition?  I only have one partition.  Would RAID settings effect this at all?

I meant to move it from a partition to another.
The boot mechanism does not mix well with RAID setups. Do you have one ?
If yes give us details.

---

### Post by Zsedcft on 2007-04-06
I have 2+0 Stripe / RAID 0.

---

### Post by ecology2007 on 2007-04-06
Our bootloader Grub does not work with stripped RAID.

---

### Post by Zsedcft on 2007-04-06
Roger that.  Will it ever work sometime in the future?

---

### Post by ago on 2007-04-06
We can only control the initrd section, but grub (grldr to be precise) has to load it up first. If grldr cannot see a drive for any reason (generally raid or fragmented kernel/initrd), there is little we can do. You can lobby the grldr developers though ;)

---

### Post by ecology2007 on 2007-04-07
> **ago said:**
> We can only control the initrd section, but grub (grldr to be precise) has to load it up first. If grldr cannot see a drive for any reason (generally raid or ***fragmented kernel/initrd***), there is little we can do. You can lobby the grldr developers though ;)

You can use contig for that, i thought using it at the end of install process, but the company who made it has been recently bought by MS :
[http://www.microsoft.com/technet/sysinternals/FileAndDisk/Contig.mspx](http://www.microsoft.com/technet/sysinternals/FileAndDisk/Contig.mspx)

---

### Post by antoinel12 on 2007-04-09
It wasns't working for me, I had this error. I moved the menu.lst from /wubi/boot/ to my C:/ root. It worked for me and I after proceeded to the instalation. The only problem I have is that I can't boot Ubuntu due to a kernel panic but I had the same problem running from the live cd so it's not because of Wubi...

---

### Post by varchar255 on 2007-04-14
> **Zsedcft said:**
> I installed wubi today, but when I select Ubuntu at the OS selection screen, it breaks at this line:
find --set-root /wubi/linux

and gives me error 17 cannot find file.

I checked the menu.lst file and everything matches up with the actual files.  How would I go about fixing this?

I have this error as well. I have an ATA drive with two partitions and Wubi is installed on the second partition. I don't have room to try moving the Wubi folder to the primary partition (unless I resize first, but I'd rather not) so I cannot try ecology's suggestion. I don't have RAID or any other special setup either. Any ideas on how I can test this?

Thanks.

---

### Post by leftyfb on 2007-04-16
Defragging helped me when I got the error.

---

### Post by varchar255 on 2007-04-16
I tried defragging but there was no effect (still got error 17). I also tried uncompressing the wubi folder (both of my two partitions are NTFS and the second partition uses the Windows compression) but that didn't help either. Any other ideas?

---

### Post by ecology2007 on 2007-04-17
It can be the compression thing. The grub bootloader has nothing specific to handle it.
You can make a copy of the wubi folder and copy it to your first partition, without the content of the disk folder if that takes too much space. Then tell us if you still have error 17.

---

### Post by varchar255 on 2007-04-19
It's working now, thanks everyone! Although I uncompressed the wubi folder, I forgot to uncompress the original ISO and I think that was the problem...but would the fact that the preseed.cfg file got erased mean the later reboots wouldn't run and I should have re-installed Wubi with every change I made, like uncompressing? In the end I uncompressed the ISO and ran a complete re-installation of Wubi and that time it worked (every other time I was just rebooting).

---

### Post by ago on 2007-04-20
> **varchar255 said:**
> It's working now, thanks everyone! Although I uncompressed the wubi folder, I forgot to uncompress the original ISO and I think that was the problem...but would the fact that the preseed.cfg file got erased mean the later reboots wouldn't run and I should have re-installed Wubi with every change I made, like uncompressing? In the end I uncompressed the ISO and ran a complete re-installation of Wubi and that time it worked (every other time I was just rebooting).

preseed.cfg is removed at installation for security reasons, it is only used during installation, if the installation fails and you want to reinstall, just run wubi again and it will recreate a preseed.cfg file. If you do not want it deleted for any reason, copy it somewhere else before rebooting.

---

