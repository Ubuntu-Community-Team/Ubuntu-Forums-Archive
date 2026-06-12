---
title: "Gparted mount point advice needed"
date: 2020-08-31
forum: General Help
---

### Post by Enigma12 on 2020-08-31
When setting up my laptop hard drive for a new distro, I used Gparted to create my / and /home partitions together. I prefer that. I want the rest of the hard drive for a data partition. To do so, I had to choose a mount point for the data partition. The options that were shown were /, /boot, /home, /tmp, /usr, /var, /srv, /opt, and /usr/local.

For the laptop, I chose /usr/local, since it seemed most appropriate to my not-extremely-knowledgeable mind. All of the OS and programs will be in / and /home.

I have read quite a few articles and watched many videos on Gparted. Many mention the mount point, but nothing that I have seen suggests which one to choose for a data partition. 

Which mount point is "best" for a partition which will be only used for storage of various files? 

Thanks in advance for any advice offered.

---

### Post by grahammechanical on 2020-08-31
You can give the data partition the name Data. I think you can do that in Gparted. It has been some years since I set up my Data partition. I have forgotten.

I have my Data partition mounted at /media/Data. So, create a folder/directory inside the media folder. I have edited /etc/fstab by adding these two lines

> # to automount Data partition
UUID=311676c4-ca3e-46d7-8b81-a1a577f601d7 /media/Data ext4 auto,users,rw,relatime 0 2

The Disks utility will give you the UUID (Universally Unique Identifier) of the Data partition.

[https://help.ubuntu.com/community/Fstab#Mount_point](https://help.ubuntu.com/community/Fstab#Mount_point)

Regards

---

### Post by oldfred on 2020-08-31
I do not think you can create the partition with the installer. You either create in advance or after install with gparted.

[http://ubuntuforums.org/showthread.php?t=2315714](http://ubuntuforums.org/showthread.php?t=2315714)
Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)

---

### Post by rbmorse on 2020-08-31
I just set up 20.04 on a new machine this afternoon.  If you use the "something else" option on the installer's partitioning options screen, you can create supplementary partitions and assign mount points on the next screen presented.

---

### Post by Impavidus on 2020-09-01
If the installer doesn't offer you the mountpoint you want, you can leave your data partition unused and fix it after installation. Just create an empty directory to use as a mountpoint and edit /etc/fstab.

[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

---

### Post by Enigma12 on 2020-09-01
Thanks to all who responded. Since no one actually answered my one question of which mount point to choose, I will do some more reading and viewing videos to learn more before trying again to make a usable data partition. I really need to learn how to do this. Once I succeed with that laptop's 160GB hard drive, I will need to create 4 data partitions on a desktop with dual 500GB hard drives. I may need to seek some advice here when I get to that. 

I have succeeded at creating fully usable data partitions in years past, but I don't remember exactly what I did then. I do know that I used chown and Disks to make the data partition usable. Have never done anything to fstab, but I have read that the Disks utility can accomplish what editing fstab accomplishes, without the potential problems that poor fstab editing can create. 

FWIW, to be here and do this, I am using an old 32-bit Pentium 4 computer running Lubuntu 18.04. Before I came here tonight, I checked the Disks and found my Data drive mounted at /media/my name/Data. Since /media is not an option in the Gparted that I recently tried on my 64-bit laptop, and I barely knew what I was doing when I set up this computer, I don't know how that happened. Maybe Gparted changed mount point options at some point. 

So, thanks again, pals. I will keep learning and enjoying Linux. Sorry, but I cannot mark this tread solved. Maybe next time I will be able to do that..

---

### Post by oldfred on 2020-09-01
You labeled your partition as Data and your file manager auto mounted it at /media/$USER/"the label or UUID of the partition"

---

