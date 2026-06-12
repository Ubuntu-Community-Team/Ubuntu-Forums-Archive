---
title: "Cloning from larger HDD to smaller external HDD"
date: 2016-05-06
forum: General Help
---

### Post by AbhimanyuAryan on 2016-05-06
```
dd if=/dev/sdX of=/dev/sdY ....
```

command doesn't work as in my case Primary HDD(with Linux) is larger and External HDD(target) is smaller

Clonezilla partition to partition cloner doesn't work. What do I try? 

500GB Primary is filled only 20GB. So, I can move to external 320GB but can't clone.....:confused:

---

### Post by him610 on 2016-05-06
My experience with using Clonezilla was successful in cloning a large drive to a smaller drive; however there is a sequence that should be followed:

**Note**: You will need to boot from an external DVD or USB storage device with a live edition of ?buntu, Knoppix, etc  to do this.

1.  [COLOR="#FF0000"]Backup all of your important data[/COLOR] from your Primary to another device, ie a USB storage device. 
2.  Boot from live media then use *gparted* to shrink the partition (to be cloned) on your Primary drive to a size less than that of your target device.
3.  Boot up on your Primary drive just to see that it will still boot. 
4.  Boot from live media then use *clonezilla* to clone the shrunken Primary drive partition to the target device.

Or
You could make a fresh of install ?buntu on the target drive.

Whichever alternative you decide on, you still have your important data.

---

### Post by sudodus on 2016-05-06
Your data fits within the smaller drive with a very good margin :-)

***0. Backup*** the most important files to some other (third) drive to avoid a disaster.

***1. rsync***

A straightforward way is to create partitions and file systems in the target drive with ***gparted*** and use ***rsync*** ```
sudo rsync -Havn source/ target
``` to copy the directory and file structure of the file system(s). After that you create swap, install the bootloader (grub), and match the content of .../etc/fstab and .../boot/grub/grub.cfg to match the new UUIDs of the partitions.

***2. Shrink and clone***

Another way is to shrink the partitions in the source drive, so that they fit within the target drive. First you should check with ```
sudo parted -ls
``` that the sector sizes are the same in the source drive and target drive. It probably is, but if not, cloning will not work.

The head end of 'main boot partition', that the bootloader points to, should ***not*** be moved. If you move it you must reinstall grub and make it point to the correct position.

After that you can use ***dd*** to clone. ***mkusb and mkusb-nox*** wrap a safety belt around dd, and can be used to clone drives

```
sudo -H mkusb /dev/sdX
```

But you should understand that this process is very slow and potentially risky. Shrinking is slow. Then it copies all drive space, also the unused space, which is a lot in your case, while the method with rsync only copies the files and directories. (Clonezilla would also skip the unused space, but I think it refuses to clone to a smaller drive. Clonezilla can clone partitions, but then you have the same manual work to fix the booting as with the rsync method.)

If it is an MSDOS partition table the target drive should work at once. You might need to run ```
sudo update-grub
``` to reach systems in moved partitions.

If it is a GUID partition table (GPT), you must also repair it, because it puts a backup table at the end of the drive. You can use ***gdisk*** for that repair, or in standard cases the [script gpt-fix](https://help.ubuntu.com/community/Installation/UEFI-and-BIOS/stable-alternative#gpt-fix), which uses gdisk under the hood.

***3. Fresh install***

Often it is easier and faster to install a fresh system and copy the personal files afterwards. Maybe you can use a ***data*** partition, that you back up separately. Another alternative is to copy the content of the /home partition to a ***home*** partition in the target drive. Then the root partition can be as small as 20-40 GB and have plenty of space for program packages and  /tmp (temporary workspace).

If you use a separate home partition, you must select ***Something else*** at the partitioning window of the installer, and specify a /home parttion. Do ***not*** let the installer format it!

***4. One Button Installer***

If your Ubuntu system is a simple system with only a root partition and a swap partition in an MSDOS partition table, you can make a tarball with the [One Button Installer](https://help.ubuntu.com/community/OBI), the script ***zmktbl***. Then you use the One Button Installer's main script to install from the tarball to the target drive.

Normally 20 GB would compress to a tarball of 5 - 10 GB, so you can use a 16 GB USB pendrive for it (or an old hard disk drive).

---

### Post by Bucky Ball on 2016-05-06
All of the above, and to add, Clonezilla works fine, but not if you're attempting to clone a partition to another that is smaller. You could say no cloning software works, including dd, as none of them will clone a larger partition to a smaller one. :-k

But we don't. ;)

---

