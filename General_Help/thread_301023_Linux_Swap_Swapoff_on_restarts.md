---
title: "Linux Swap Swapoff on restarts"
date: 2006-11-16
forum: General Help
---

### Post by Chazall1 on 2006-11-16
I have noticed that each time I restart my system, my linux swap partition is not on, I must use G-parted to Swapon at every re-boot or restart. This might have been occuring when I upgraded to Edgy from Dapper on Ocr 25th. I have lost my Usplash and have a Blank screen after grub to my login screen. I removed Usplash and I began seeing text during the boot process. I read that the Swap was not available. 

Any Ideas???

Thanks

---

### Post by Ramses de Norre on 2006-11-16
Is it in /etc/fstab?

---

### Post by Chazall1 on 2006-11-16
I just rebooted, and looked in the /etc/fstab.
My swap is hda7 on my system.
Here is the info before I swapon with gparted
UUID=06vvb261-6dga-4c08-a176-1d282e 6fdc85 none swap sw 0 0

---

### Post by Chazall1 on 2006-11-19
Any Ideas on how go get the Swap partition to mount on start-up?

---

### Post by jjross on 2006-11-20
your etc/fstab should look something like this

/dev/hda7       none            swap    sw              0       0

---

### Post by CatKiller on 2006-11-20
> **jjross said:**
> your etc/fstab should look something like this

/dev/hda7       none            swap    sw              0       0

Actually, Edgy puts in the UUID= identifiers instead. I don't know if that's relevant to the OP though.

---

### Post by anaconda on 2006-11-20
> **CatKiller said:**
> Actually, Edgy puts in the UUID= identifiers instead. I don't know if that's relevant to the OP though.

Yep, but both ways still work in edgy. I recommend the old way, because then you can be sure thet you have the right partition in your fstab -file.

And Why do you have to use qtparted to put swap on?

in terminal type:
sudo swapon /dev/hda7

and you can check before/after that it is on with 
free

---

### Post by Chazall1 on 2006-11-21
I have tried both ways, with the UUID=  and the dev/hda7. When I re-boot my swap is OFF. I have also added RESUME=/dev/hda7 in /etc/initramfs-tools

When I re-boot, SWAPOFF! 

And this one seemed easy to correct?????
Mr. Frustrated!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!1

---

### Post by taurus on 2006-11-21
Let's have a look at your /etc/fstab (the whole thing) and the output of this command from a terminal!

```
sudo fdisk -l
cat /etc/fstab
```

---

### Post by Chazall1 on 2006-11-21
Here.

Disk /dev/hda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1           6       48163+  de  Dell Utility
/dev/hda2   *           7        3922    31455270    7  HPFS/NTFS
/dev/hda3            3923        4281     2883667+  db  CP/M / CTOS / ...
/dev/hda4            4282        9726    43736962+   5  Extended
/dev/hda5            4282        6971    21607393+  83  Linux
/dev/hda6            6972        9595    21077248+  83  Linux
/dev/hda7            9596        9726     1052226   82  Linux swap / Solaris
cdlish@cdlish-desktop:~$ 

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda6 -- converted during upgrade to edgy
UUID=8bd36f06-7967-47e4-9933-669abf52b03f / ext3 defaults,errors=remount-ro 0 1
# /dev/hda5 -- converted during upgrade to edgy
UUID=18c79eac-b4e4-4fea-a502-786ce82af86e /home ext3 defaults 0 2
# /dev/hda1 -- converted during upgrade to edgy
UUID=07D4-0C0C /media/hda1 vfat defaults,utf8,umask=007,gid=46 0 1
# /dev/hda2 -- converted during upgrade to edgy
UUID=CAF012F3F012E58B /media/hda2 ntfs-3g silent,umask=0,locale=en_US.utf8,no_def_opts,allow_other 0 0
/dev/hda3       /media/hda3     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/hda7 none swap sw 0 0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
cdlish@cdlish-desktop:~$ 

I had it working I think once, I tried to Hibernate, said it failed, did a re-boot and no SwapON

---

### Post by taurus on 2006-11-21
> **Chazall1 said:**
> Here.

Disk /dev/hda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1           6       48163+  de  Dell Utility
/dev/hda2   *           7        3922    31455270    7  HPFS/NTFS
/dev/hda3            3923        4281     2883667+  db  CP/M / CTOS / ...
/dev/hda4            4282        9726    43736962+   5  Extended
/dev/hda5            4282        6971    21607393+  83  Linux
/dev/hda6            6972        9595    21077248+  83  Linux
/dev/hda7            9596        9726     1052226   82  Linux swap / Solaris
cdlish@cdlish-desktop:~$ 

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda6 -- converted during upgrade to edgy
UUID=8bd36f06-7967-47e4-9933-669abf52b03f / ext3 defaults,errors=remount-ro 0 1
# /dev/hda5 -- converted during upgrade to edgy
UUID=18c79eac-b4e4-4fea-a502-786ce82af86e /home ext3 defaults 0 2
# /dev/hda1 -- converted during upgrade to edgy
UUID=07D4-0C0C /media/hda1 vfat defaults,utf8,umask=007,gid=46 0 1
# /dev/hda2 -- converted during upgrade to edgy
UUID=CAF012F3F012E58B /media/hda2 ntfs-3g silent,umask=0,locale=en_US.utf8,no_def_opts,allow_other 0 0
/dev/hda3       /media/hda3     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/hda7 none swap sw 0 0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
cdlish@cdlish-desktop:~$ 

I had it working I think once, I tried to Hibernate, said it failed, did a re-boot and no SwapON
No wonder your swap, /dev/hda7, is not mounted because you have a # sign in front of it!!!  Any line with a # in front is a command and it will not be looked at.  Therefore, edit your /etc/fstab and remove the # from /dev/hda7.  Then, either reboot or mount it again with

```
sudo mount -a
free
```

---

### Post by Chazall1 on 2006-11-21
The Simple things, I was looking at all the writen Info that Edgy added and did not think about the #  It works, thanks, You dont know anything about Usplash????  Boy I have tried Everything, Everything in the forums, ???????????????????????

Thank You

---

### Post by taurus on 2006-11-21
What about usplash!  Maybe you should create a new thread then since this topic is solved.

---

