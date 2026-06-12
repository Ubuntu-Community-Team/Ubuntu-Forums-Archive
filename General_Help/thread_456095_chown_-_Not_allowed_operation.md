---
title: "chown - Not allowed operation"
date: 2007-05-27
forum: General Help
---

### Post by Cecilio on 2007-05-27
Hi, I'm new to linux. :)

I have a shared partition (windows and Ubuntu) mounted as /media/sdb1.
I am trying to change the owner of one folder on it: /media/sdb1/usr. So I do:

cecilio@homer:/media/sdb1$ sudo chown cecilio ./usr

and i get:

chown: cambiando el propietario de `./usr': Operación no permitida
[translation: chown: changing the owner of './usr': Not allowed operation]

What I am doing wrong? How should i do it?

Thank you
Cecilio

---

### Post by Bachstelze on 2007-05-27
Which filesystem is the partition formatted in ?

---

### Post by Cecilio on 2007-05-27
It is FAT32

---

### Post by Bachstelze on 2007-05-27
Then it's normal. FAT32 does not support changing file permissions.

---

### Post by Cecilio on 2007-05-27
Then, what should I do to have control of my files? 
I need to share this partition with WinXP !

Merci,

---

### Post by taurus on 2007-05-27
How do you mount /dev/sdb1, automount, by hand, or through /etc/fstab?

---

### Post by earobinson on 2007-05-27
can you post your /etc/fstab file?

---

### Post by Cecilio on 2007-05-27
Hi,

Sorry, I don't know how is it mounted. Ubuntu does it for me. It was automatically configured that way when I installed Ubuntu, and I do not have enough knowledge yet 

This is the etc/fstab file:
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=6422055c-3961-4d4b-8960-c6ca4faf1b4a /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda4
UUID=6047852e-6936-4f80-ab3a-38c8f9341f1d /home           ext3    defaults        0       2
# /dev/sdb1
UUID=4605-4F3A  /media/sdb1     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda2
UUID=523c5c50-27d1-474b-a8b2-47f0df4096a7 none            swap    sw              0       0
/dev/cdrom        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0

```

Thank you,

---

### Post by Cecilio on 2007-05-28
Any help please?

---

### Post by taurus on 2007-05-28
What filesystem is /dev/sdb1?  Which release are you running:  Dapper, Edgy, or Feisty?  Post the output of this command?

```
sudo fdisk -l
```

---

### Post by Cecilio on 2007-05-30
Sorry for the delay. I've been very busy since Sunday.

The file system is FAT32. The system is Ubuntu 7.04

And here is the output of fdisk -l

```

cecilio@homer:~$ sudo fdisk -l
Password:

Disco /dev/sda: 160.0 GB, 160041885696 bytes
255 cabezas, 63 sectores/pista, 19457 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sda1               1        3916    31455238+  83  Linux
/dev/sda2            3917        4438     4192965   82  Linux swap / Solaris
/dev/sda3   *        4439        9660    41945715    7  HPFS/NTFS
/dev/sda4            9661       19457    78694402+  83  Linux

Disco /dev/sdb: 250.0 GB, 250059350016 bytes
255 cabezas, 63 sectores/pista, 30401 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sdb1               1       30401   244196001    b  W95 FAT32


```

Thank you for your time.

Regards,

---

### Post by taurus on 2007-05-30
Try

```
sudo umount /dev/sdb1
sudo mount -t vfat /dev/sdb1 /media/sdb1 -o iocharset=utf8,umask=000
ls -la /media
```
See if you can write to /media/sdb1 now.

---

### Post by Cecilio on 2007-05-30
sudo umount /dev/sdb1 fails:
```

cecilio@homer:~$ sudo umount /dev/sdb1
umount: /media/sdb1: dispositivo ocupado  *[translation: device busy]*
umount: /media/sdb1: dispositivo ocupado

```



It is open only gnome and a terminal window

---

### Post by taurus on 2007-05-30
Are you currently in /media/sdb1 or do you have something open in /media/sdb1?  You need to close everything down, nautilus or whatever else, and then run

```
cd ~
sudo umount /dev/sdb1
sudo mount -t vfat /dev/sdb1 /media/sdb1 -o iocharset=utf8,umask=000
ls -la /media
```

---

### Post by Cecilio on 2007-05-30
I have open only gnome and a terminal window. 

sdb1 is a shared disk only with data. Shouldn't be in use in these conditions. but ... i know practically nothing about linux.

How can I close gnome and have just a terminal session?

---

### Post by taurus on 2007-05-30
Open a terminal, Applications -> Accessories -> Terminal, and run those three commands.

---

### Post by Cecilio on 2007-05-30
> Open a terminal, Applications -> Accessories -> Terminal, and run those three commands.

That's what i am doing. But perhaps gnome is somehow using device sdb1. if i could close everything and work just on a native terminal session .. Do you know how to do this?

---

### Post by taurus on 2007-05-30
You can log out of Gnome.  Then, press <Ctrl><Alt>F2 and log in with your username and password.  Then, run those commands from a prompt and see what happens.

---

### Post by Cecilio on 2007-05-30
On a native terminal it works. The mount command gives a warning about using utf8 with fat32, as all filenames will be case sensitive.

I can not copy here the output. I don't know how to do it from a terminal session and to save it into a file

Then i tried

sudo chown cecilio /media/sdb1

but no sucess. The same error. 

How do I return to Gnome from the terminal ? I had to restart the computer :oops:

---

### Post by taurus on 2007-05-30
<Alt>F7 to get back to GUI login screen.

---

### Post by psusi on 2007-05-30
> **Cecilio said:**
> 
sudo chown cecilio /media/sdb1

but no sucess. The same error. 



Yes, as was stated before, fat32 does not have any concept of permissions so you can not set them.  You should be able to access the files now though.

---

### Post by Cecilio on 2007-05-30
> fat32 does not have any concept of permissions so you can not set them.

Yes, at least in Windows. But that would explain any issues with permissions, and I am trying to change the owner. Linux displays owner information. Where is this info. stored and how to change it? ;)

All this was originated because I wrote a bash script and tried to give it execution permissions. As i didn't succeed, I thought about changing the owner to do it.

Thank you all of you for your time and help, 

Although I couldn't solve the problem, at least i have learned many things, such as opening a closing a terminal session. :D

Thank you all.
Best regards,

---

### Post by psusi on 2007-05-30
> **Cecilio said:**
> Yes, at least in Windows. But that would explain any issues with permissions, and I am trying to change the owner. Linux displays owner information. Where is this info. stored and how to change it? ;)

All this was originated because I wrote a bash script and tried to give it execution permissions. As i didn't succeed, I thought about changing the owner to do it.

Thank you all of you for your time and help, 

Although I couldn't solve the problem, at least i have learned many things, such as opening a closing a terminal session. :D

Thank you all.
Best regards,

Owner is included in permissions.  FAT does not store any of this information, so linux has to just make it up, based on the mount options you set in your fstab or give on the mount command line.

---

