---
title: "Ubuntu cleared my Hard drive!!!"
date: 2007-09-18
forum: General Help
---

### Post by Valkyrie Wrath on 2007-09-18
I was installing it from the bootloader I got in the mail and it removed everything with out asking. WTF? is there any way to undo this?HELP!!!

---

### Post by treis on 2007-09-18
What did you do?

---

### Post by Valkyrie Wrath on 2007-09-18
all I did was run the dick then when I got to the Ubuntu desktop I clicked install and got part way through but I canceled it before it finished

---

### Post by treis on 2007-09-18
Eject the CD and reboot.

---

### Post by Valkyrie Wrath on 2007-09-18
I did. when I boot ubuntu and look at the hard drive it says 32 of 35.5 GB

---

### Post by strabes on 2007-09-18
The default option erases your entire hard drive. It tells you this.

---

### Post by Valkyrie Wrath on 2007-09-18
well I quit out of the install before it got to the partition thing. I thought it erased the HDD but I just checked and on the Hard drive it said something around 4 GB left and it was around that before. But when I try to boot without the ubuntu disk in it has a blank screen with an error message(I forgot what it said). What do I boot from for XP? When I press f12 at the startup it brings me to the blue screen where I can change the options and the boot settings. there is like 4 options. which one do I choose? I've tried each one and they all act like its looking for a disk to boot.

---

### Post by Valkyrie Wrath on 2007-09-18
the message said bad PDR

---

### Post by Valkyrie Wrath on 2007-09-20
why dont they atleast prompt me about it erasing my hard drive? why would anyone want that? Now I'm in deep **** because of this. I didnt even finish the partition part of the installation

---

### Post by treis on 2007-09-21
Are you sure it doesn't say bad PBR? 

If it does, boot up with your Windows CD into a recovery console and type fixmbr.

---

### Post by jfinkels on 2007-09-21
You should be able to access any data stored on your hard drives (if you didn't choose to overwrite it with your initial installation) from the Live CD environment. To view partitions on your disk, type the following in the terminal:```
sudo fdisk -l
```You will see a listing of the names of your partitions, usually they look like "/dev/hda1" "/dev/sda2", or something like that.

To mount the drives, first make a directory to mount the drive on by typing:```
sudo mkdir /mnt/mydrive
``` and then mount the drive using the following command:```
sudo mount /dev/sda1 /mnt/mydrive
```replacing "/dev/sda1" with the partition that you want to mount as discovered from the fdisk -l command.

Once you mount the partition, you should be able to check what data is there by navigating to the directory:```
cd /mnt/mydrive
```and listing contents```
ls
``` You can also do this using the graphical file manager, Nautilus.

If you want to reinstall the default Windows MBR (Master Boot Record), which allow you to boot directly into Windows, you will need your Windows install disk.

If you want to reinstall GRUB so that you have a choice about which partition to boot from when you turn on your computer, you will need to use Super Grub Disk ( [http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/) ), or just install Ubuntu again, which automatically writes GRUB to your MBR.

---

### Post by treis on 2007-09-21
Be warned though that if you install Ubuntu it will erase everything on the partition you install it to.

---

### Post by Judgegeo on 2007-09-21
Aha. My advice, learn to read next time. Dont click "DELETE MY DATA PLZ" if you dont mean it.

---

