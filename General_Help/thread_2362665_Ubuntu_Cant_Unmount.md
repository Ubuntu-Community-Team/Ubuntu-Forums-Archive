---
title: "Ubuntu Cant Unmount"
date: 2017-05-31
forum: General Help
---

### Post by doomsdaystar on 2017-05-31
Doesnt seem to want to let me unmount this partition its my only one
/dev/sda1 also says
 #umount -v "/"
umount: /: target is busy
(In some cases useful info about processes that use the device is found
by lsof(8) or fuser(1) .)

also says its mounted at file system root

---

### Post by deadflowr on 2017-05-31
It's unwise to attempt to unmount the running file system.
Best to run a separate operating system, livedvds work, to have the file system in question unmounted.

---

### Post by doomsdaystar on 2017-05-31
im just trying to make part of this partition to be ntfs thats all

---

### Post by QIII on 2017-05-31
Hello!

It might be helpful if we knew what your end goal in doing this is.  I think you may have some misconception.

Edit: Apparently we were typing at the same time.

---

### Post by doomsdaystar on 2017-05-31
im to trying to unmount this partition then format the disk as ntfs

so that i can install windows 10 since the whole hardrive doesnt support the files currently

so can you help me?

---

### Post by yancek on 2017-05-31
> so can you help me?         

As pointed out in the post above by deadflowr, you can not unmount or resize a partition on which you are running so use your Ubuntu DVD/flash drive that you used to install and open the GParted partition manager and resize/shrink the Ubuntu partition.

I'm not sure why you would need to do this.  You should be able to boot the windows DVD and just select whatever option it has to overwrite and format everything and install windows.  Is that what you want, to overwrite Ubuntu with windows. 

> so that i can install windows 10 since the whole hardrive doesnt support the files currently

What??  The hard drive doesn't support what files?

---

### Post by doomsdaystar on 2017-05-31
im not using dvd im using a usb windows 10 i bought from best buy

---

### Post by SeijiSensei on 2017-05-31
If you want to keep Linux, you'll need an ext4 partition.  Linux cannot use NTFS because it lacks important primitives like POSIX permissions.

You'll have a harder time installing Windows onto a system with an existing Linux distribution than the other way round.  Windows will overwrite the boot sector making any Linux partitions disappear.  If you want to run both Windows and Linux on the same machine, you should install Windows now then install Ubuntu.

You cannot make changes to mounted filesystems.  You can boot from an Ubuntu installation disk and choose "Try Ubuntu" when the menu appears.  Then you'll be able to run something like gparted and make any changes you need to your hard disk.

---

### Post by yancek on 2017-05-31
> so can you help me?         

As pointed out in the post above by deadflowr, you can unmount or resize a partition on which you are running so use your Ubuntu DVD/flash drive that you used to install and open the GParted partition manager and resize/shrink the Ubuntu partition.

I'm not sure why you would need to do this.  You should be able to boot the windows DVD and just select whatever option it has to overwrite and format everything and install windows.  Is that what you want, to overwrite Ubuntu with windows. 

> so that i can install windows 10 since the whole hardrive doesnt support the files currently

What??  The hard drive doesn't support what files?  Do you have some windows programs you can't run on Ubuntu?

---

### Post by doomsdaystar on 2017-05-31
> **SeijiSensei said:**
> If you want to keep Linux, you'll need an ext4 partition.  Linux cannot use NTFS because it lacks important primitives like POSIX permissions.

You'll have a harder time installing Windows onto a system with an existing Linux distribution than the other way round.  Windows will overwrite the boot sector making any Linux partitions disappear.  If you want to run both Windows and Linux on the same machine, you should install Windows now then install Ubuntu.

You cannot make changes to mounted filesystems.  You can boot from an Ubuntu installation disk and choose "Try Ubuntu" when the menu appears.  Then you'll be able to run something like gparted and make any changes you need to your hard disk.
What if i dont want to keep linux and wanted only windows?

---

### Post by oldos2er on 2017-05-31
Boot into Windows, restore Windows' boot loader, reboot to make certain it's working and grub is gone, then you can format any unwanted Linux partitions. I'm assuming you don't want any of the data on your Linux partitions, because this process will destroy it all.

---

### Post by doomsdaystar on 2017-05-31
> **oldos2er said:**
> Boot into Windows, restore Windows' boot loader, reboot to make certain it's working and grub is gone, then you can format any unwanted Linux partitions. I'm assuming you don't want any of the data on your Linux partitions, because this process will destroy it all.
how can i do that since everytime i want to install windows 10 it says that the hdd im using is using the wrong files ext4 not ntfs and i cant change that since its already running the only partition with my system files

---

### Post by kurt18947 on 2017-05-31
I'm trying to follow this thread. Do you, doomsdaystar want to keep Ubuntu/Linux in any way, or do you want it gone completely? If you want to set up dual boot so you can choose Windows or Linux at startup, I think you'll find it easier to install Windows first then Ubuntu/Linux as suggested by SeijiSensei. There is a boot repair disk floating around that would restore dual boot capability after installing Windows but I don't believe that works with current version Ubuntu. It wouldn't work when I tried it.

---

### Post by doomsdaystar on 2017-05-31
> **kurt18947 said:**
> I'm trying to follow this thread. Do you, doomsdaystar want to keep Ubuntu/Linux in any way, or do you want it gone completely? If you want to set up dual boot so you can choose Windows or Linux at startup, I think you'll find it easier to install Windows first then Ubuntu/Linux as suggested by SeijiSensei. There is a boot repair disk floating around that would restore dual boot capability after installing Windows but I don't believe that works with current version Ubuntu. It wouldn't work when I tried it.
want it gone

---

### Post by yancek on 2017-05-31
From your windows 'usb' booted, you should have an option to install windows using the entire disk.  That's basically been the default for windows for 30+ years.  If you get a message indicating it doesn't have an ntfs filesystem you should surely be able to format it as ntfs as that is a proprietary windows filesystem.  There should be no reason to 'unmount' the Ubuntu partition or do anything with it if all you want to do is install windows using the whole drive. 

Also, it doesn't matter what the installation media is, CD/DVD/usb drive.

---

### Post by oldos2er on 2017-05-31
> **doomsdaystar said:**
> how can i do that since everytime i want to install windows 10 it says that the hdd im using is using the wrong files ext4 not ntfs and i cant change that since its already running the only partition with my system files

My bad, I thought you had Windows installed already.

I don't know anything about installing Windows, but isn't there an option to format your disk prior to installing it?

---

