---
title: "Grub Error 15"
date: 2008-06-02
forum: General Help
---

### Post by illbashu on 2008-06-02
> To make a backup a copy of the existing menu.lst file use:

cp /boot/grub/menu.lst /boot/grub/menu.lst.old

You can try re-installing the grub using the Ubuntu Live CD, in two different ways.
GUI

   1.

      Boot your computer up with Ubuntu CD
   2.

      Go through all the process until you reach "[!!!] Disk Partition"
   3.

      Select Manual Partition
   4.

      Mount your appropriate linux partions

 /
 /boot
 swap
 ..... 

   5.

      DO NOT FORMAT THEM.
   6.

      Finish the manual partition
   7.

      Say "Yes" when it asks you to save the changes
   8.

      It will give you errors saying that "the system couldn't install ....." after that
   9.

      Ignore them, keep select "continue" until you get back to the Ubuntu installation menu
  10.

      Jump to "Install Grub ...."
  11.

      Once it is finished, just restart your computer

Command line

   1.

      Boot your computer up with Ubuntu CD
   2.

      Open a terminal window or switch to a tty.
   3.

      Go SuperUser (that is, type "sudo -s"). Enter root passwords as necessary.
   4.

      Type "grub"
   5.

      Type "find /boot/grub/stage1". You'll get a response like "(hd1,0)". Use whatever your computer spits out for the following lines.
   6.

      Type "root (hd1,0)", or whatever your harddisk + boot partition numbers are for Ubuntu.
   7.

      Type "setup (hd1,0)", ot whatever your harddisk nr is.
   8.

      Quit grub by typing "quit".
   9.

      Reboot and remove the bootable CD.

[https://help.ubuntu.com/community/GrubHowto](https://help.ubuntu.com/community/GrubHowto)

i am trying to do the command line way, booted up my comp on my ubuntu 8.04 boot cd and i got to the part 5 and i didn't get (hd1,0) or anything like that i got an error saying 
```
Error 15: File not found
```

---

### Post by geirha on 2008-06-02
Does ```
sudo fdisk -l
``` list the harddrive and partitions ubuntu is installed on?

---

### Post by illbashu on 2008-06-02
```
root@ubuntu:~# sudo fdisk -l

Disk /dev/sda: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000cb6b2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       30233   242846541   83  Linux
/dev/sda2           30234       30515     2265165    5  Extended
/dev/sda5           30234       30515     2265133+  82  Linux swap / Solaris

Disk /dev/sdb: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x15f415f3

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        4997    40138371    7  HPFS/NTFS
```

just throughing this out there... 

```
ubuntu@ubuntu:~$ ls /boot/grub
ls: cannot access /boot/grub: No such file or directory
```

---

### Post by meierfra. on 2008-06-03
We need more information. What happens during boot up? Does the grub menu appear?   Do you get any  error messages?
Did you have any error messages during installation?

Also post  the output of the following commands:

```
sudo mkdir  /ubuntu
sudo mount -t ext3 /dev/sda1 /ubuntu
cd /ubuntu/boot
ls 
ls  grub/
sudo cat grub/menu.lst 
```
(lst is short for list)

---

### Post by illbashu on 2008-06-03
```
ubuntu@ubuntu:~$ sudo mkdir  /ubuntu
ubuntu@ubuntu:~$ sudo mount -t ext3 /dev/sda1 /ubuntu
ubuntu@ubuntu:~$ cd /ubuntu/boot
bash: cd: /ubuntu/boot: No such file or directory
ubuntu@ubuntu:~$ ls 
Desktop  Documents  Music  Pictures  Public  Templates  Videos
ubuntu@ubuntu:~$ ls  grub/
ls: cannot access grub/: No such file or directory
ubuntu@ubuntu:~$ sudo cat grub/menu.lst
cat: grub/menu.lst: No such file or directory
ubuntu@ubuntu:~$ 
```

the installation was smooth. when my comp boots off the hardrive grub screen comes up and says loading then i get error 15, and i cant do anything but alt-ctrl-delete to restart comp... btw this started happening after the last fsck...

---

### Post by meierfra. on 2008-06-03
Go to "Places->Computer". One of the icon is for Ubuntu. Double click it. See whether you have a "boot" folder. 

Maybe also do

```
sudo mkdir  /ubuntu
sudo mount -t ext3 /dev/sda1 /ubuntu
ls /ubuntu

```
and see whether "boot" appears on the list.

---

