---
title: "Using the other harddrive?"
date: 2008-04-30
forum: General Help
---

### Post by loop444 on 2008-04-30
I used Gparted to format my other 200GB harddrive, now I want to use it to copy files to and be able to make folders in it, but i cant, i can enter it however. It is ext3 and I cant change "writeprotected" to "write and read rights" in properties manually. Im noob. What to do? :popcorn:

---

### Post by loop444 on 2008-04-30
Bump

---

### Post by loop444 on 2008-04-30
Bump

---

### Post by forestpixie on 2008-04-30
It probably isn't mounted in fstab 

can you run these 2 in a terminal and post the output and I'll try to help

```
cat /etc/fstab
sudo fdisk -l
```

If you're going to bump you're threads try and wait at least 24 hours - certainly not 11 minutes. I realise you're getting frustrated but..

---

### Post by loop444 on 2008-05-02
> **forestpixie said:**
> It probably isn't mounted in fstab 

can you run these 2 in a terminal and post the output and I'll try to help

```
cat /etc/fstab
sudo fdisk -l
```

If you're going to bump you're threads try and wait at least 24 hours - certainly not 11 minutes. I realise you're getting frustrated but..

Ok, thank you, the double bump was some kind of flux. Btw, maybe you can suggest a paypal or some kind of donate button for posts, it would be nice to be able to donate, even if just a tiniest amount, as thanks for the help. Generally, overally, always.

starship@starship-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=9cf42fdc-c8b7-4037-a7eb-f8a9872ca19f /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=8286402a-e1c6-4553-91f3-9fedcb1b99c2 none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/hdc        /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
starship@starship-desktop:~$ sudo fdisk -l
[sudo] password for starship:

Disk /dev/sda: 200,0 GB, 200049647616 byte
255 huvuden, 63 sektorer/spår, 24321 cylindrar
Enheter = cylindrar av 16065 · 512 = 8225280 byte
Diskidentifierare: 0x000e7aee

    Enhet Start     Början        Slut     Block    Id  System
/dev/sda1   *           1       23944   192330148+  83  Linux
/dev/sda2           23945       24321     3028252+   5  Utökad
/dev/sda5           23945       24321     3028221   82  Linux växling / Solaris

Disk /dev/sdb: 200,0 GB, 200049647616 byte
255 huvuden, 63 sektorer/spår, 24321 cylindrar
Enheter = cylindrar av 16065 · 512 = 8225280 byte
Diskidentifierare: 0x1a1bbfee

    Enhet Start     Början        Slut     Block    Id  System
/dev/sdb1               1         521     4184901   83  Linux
/dev/sdb2             522       24321   191173500   83  Linux
starship@starship-desktop:~$ 

:confused:

---

### Post by forestpixie on 2008-05-02
This should work to get it mounted on boot, we can edit the fstab and add the partitions to it. I assume that you want to add the 2 partitions on the second hdd. I have no idea what Utökad means - but guess it's nothing to do with Linux - if that isn't the case post back, similarly if it's not the partitions on the second drive you want mounted.

Backup the file to start with 

```
sudo cp /etc/fstab /etc/fstab.0205
```

Make 2 folders to mount them in

```
sudo mkdir /media/drive1
sudo mkdir /media/drive2
```
You can change drive1 and drive2 to what ever you want as long as you make same changes to the fstab lines and in the chmod and chown commands.

We will edit fstab using nano in the terminal - to save file Ctrl+O plus enter, then Ctrl+X to exit

```
sudo nano /etc/fstab
```
File is now open for editing - be careful that you only change what you want to change - add the folders you want to mount using these lines at the end of the file

```
/dev/sdb1 /media/drive1 ext3 defaults 0 0
/dev/sdb2 /media/drive2 ext3 defaults 0 0
```

Save and close the file - mount the 2 partitions 

```
sudo mount -a
```

For permissions (I've got this from [psychocats]("http://www.psychocats.net/ubuntu/mountlinux") site - a good resource! )

I assume your username is starship - if not change in these commands

```
sudo chown -R starship:starship /media/drive1
sudo chmod -R 755 /media/drive1
sudo chown -R starship:starship /media/drive2
sudo chmod -R 755 /media/drive2
```

Donate to your choice of software - not Windows though of course :)

I'll be happy to have made you happy.

---

### Post by loop444 on 2008-05-02
> **forestpixie said:**
> 
Donate to your choice of software - not Windows though of course :)

I'll be happy to have made you happy.

Thank You, It Worked :KS :guitar:

---

### Post by forestpixie on 2008-05-02
:biggrin:

I'm happy then

---

