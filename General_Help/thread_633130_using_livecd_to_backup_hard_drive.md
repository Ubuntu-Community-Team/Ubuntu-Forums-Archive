---
title: "using livecd to backup hard drive"
date: 2007-12-06
forum: General Help
---

### Post by ELD on 2007-12-06
Hi all i buggered up my pc really bad and need to backup some files from an ext3 partition, but when booting in the live cd all files and folders on this partition are locked so i can't transfer them to my usb stick

any ideas?!

---

### Post by barney_1 on 2007-12-06
What are you doing to access your partitions?

You need to mount your drives, find out what address each partition is at by typing:
```
sudo fdisk -l
```

Find which address your partition is at (for example, mine is /dev/sda1):
```
sudo mkdir /mnt/mydrive
sudo mount /dev/sda1 /mnt/mydrive
cd /mnt/mydrive
ls
```

The commands above should make a directory (/mnt/mydrive) and mount your messed up drive to it.  Just make sure you replace the /dev/sda1 with your relevant drive.

You should then be able to copy files over to you usb drive which should automount in the /media folder when you plug it into the usb port.

---

### Post by ELD on 2007-12-07
It auto mounts to "disk" in media because it is ext3 ubuntu auto mounts it so what do i do?

---

### Post by barney_1 on 2007-12-07
If you can post some of the output you've gotten that would help.

You should be able to use the command line to copy your files over to your usb drive. I'm going to assume that you manually mounted your hdd partition to /mnt/mydrive and your usb drive is at /media/disk

The following will create a "home" folder on your usb drive and the copy everything in the home directory on you hdd over to it.  Modify this code is any way to wish to get only the files you want.  The flag "-R" used with the cp command will copy the subdirectories and their contents as well as all the files in the given directory.

```
cd /media/disk
mkdir home
cd home
sudo cp -R /mnt/mydrive/home/* .
```

---

### Post by ELD on 2007-12-22
> **barney_1 said:**
> If you can post some of the output you've gotten that would help.

You should be able to use the command line to copy your files over to your usb drive. I'm going to assume that you manually mounted your hdd partition to /mnt/mydrive and your usb drive is at /media/disk

The following will create a "home" folder on your usb drive and the copy everything in the home directory on you hdd over to it.  Modify this code is any way to wish to get only the files you want.  The flag "-R" used with the cp command will copy the subdirectories and their contents as well as all the files in the given directory.

```
cd /media/disk
mkdir home
cd home
sudo cp -R /mnt/mydrive/home/* .
```

I said before ubuntu auto-mounts it so i dont know how to unmount it and then re-do it.

---

### Post by NotRoot:-) on 2007-12-22
umount /mnt/hda5
or  sudo umount /mnt/hda5

would unmount partition #5 on drive a, for example.


From [http://www.ibm.com/developerworks/linux/library/l-knopx.html](http://www.ibm.com/developerworks/linux/library/l-knopx.html)
ISystem recovery with Knoppix is a good guide.
Most of the commands are similar for Ubuntu.

---

### Post by ELD on 2007-12-24
For one thing it won't let me unmount anything because i'm on the livecd so the entries are not in the fstab, i can't install as it says my partition i want to backup has uncorrected errors when it works perfectly (u haven't even touched it!).

I try to resize my other hard drive but it just sits and does a whole lot of nothing.

Here is a picture of my drive to backup (as you can see all files are bloody padlocked grrr, so i can't touch them :():
[[IMG]http://img512.imageshack.us/img512/9237/screenshot1filebrowservp5.th.png[/IMG]](http://img512.imageshack.us/my.php?image=screenshot1filebrowservp5.png)

The livecd auto-mounts my 160gb sata drive, and doesnt let me touch it, and i cant unmount anything as its a livecd and it says the entries are not in the fstab!

Please help!

---

