---
title: "Try to install a full encrypt ubuntu installation"
date: 2017-06-23
forum: General Help
---

### Post by frenchuser on 2017-06-23
Hello, 

First sorry for my language i am not English .

Like a say in the title i am try  to install a full encrypt ubuntu installation but i have a problem with the follow command ( i am follow a tutorial ) : 

```
ubuntu@ubuntu:~$ sudo mount /dev/mapper/vgubuntu-root /mnt
ubuntu@ubuntu:~$ sudo mount /dev/sda1 /mnt/boot/efi

ubuntu@ubuntu:~$ sudo mount --bind /dev /mnt/dev
ubuntu@ubuntu:~$ sudo mount -t proc /proc /mnt/proc
ubuntu@ubuntu:~$ sudo mount --bind /run /mnt/run
ubuntu@ubuntu:~$ sudo mount -t sysfs /sys /mnt/sys
```
When i am try the first one it is work but my partition is mount in a folder name "@" and not just mount in /mnt so if i want the others command work i have for exemple tape this :

```
ubuntu@ubuntu:~$ sudo mount /dev/sda1 /mnt/@/boot/efi
```

and then the other command work but at the final of my tutorial, when i have to install GRUB : 

```
grub-install /dev/sda
```

i have an error : grub-install error cannot find /boot/efi, is DEV/? mount  ( is not the exactly message but it seem like this ) .

So if anyone can help me or explain why my partition is not directly mount in /mnt, Thanks .

---

### Post by deadflowr on 2017-06-23
Is this a btrfs file system setup?
Also, post a link to the tutorial, please.

---

### Post by frenchuser on 2017-06-23
Hello thanks to answer, 

this is the tutorial [https://soozx.fr/ubuntu-1704-chiffre-boot-compris-uefi/ubuntu-chiffre-boot-compris-installation-configuration-grub/](https://soozx.fr/ubuntu-1704-chiffre-boot-compris-uefi/ubuntu-chiffre-boot-compris-installation-configuration-grub/) 

yes i was choose BTRFS file system but in the tutorial is tell to choose EXT4 and i choose BTRFS because i have read it is beter to EXT4 for many thing and particularly for disk image and i need this .

can is work with BTRFS  ?

PS; The tutorial is in French .

---

### Post by yancek on 2017-06-23
I think you would have more success if you created separate mount points under the /mnt directory for your root filesystem partition and your efi partition.  Your commands show you are mounting to the same mount point.  Also make sure you have the correct location and partition of the efi partition.  An example would be:

sudo mkdir /mnt/vgubuntu-root
sudo mkdir /mnt/efi

Then run your separate mount command to those mount points.  I'm not familiar with LVM so I'm not sure if you have or need a separate boot partition.  I don't understand the part about the "@", did that happen automatically or did you enter that as part of the command?

---

### Post by frenchuser on 2017-06-23
Hello, 

So i have solved my problem, it is come from the BTRFS Format, know it is work, i have see on a other furum the BTRFS is not yet compatible with GRUB2, so i have install my system in EXT4 .

So thanks for all your help, goodbye .

---

