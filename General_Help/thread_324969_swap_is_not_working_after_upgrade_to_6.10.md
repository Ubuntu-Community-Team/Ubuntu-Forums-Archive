---
title: "swap is not working after upgrade to 6.10"
date: 2006-12-24
forum: General Help
---

### Post by ryan00davis on 2006-12-24
im running kubuntu 6.10 (upgraded from 6.06) and my swap appears to not be on at all.  if i run command "free" i get this on the swap partition
```
Swap:            0          0          0
```

my fstab looks like this:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda6 -- converted during upgrade to edgy
UUID=3e5cefbb-074c-49a6-af5f-6684ed888ceb / ext3 defaults,errors=remount-ro 0 1
# /dev/hda3 -- converted during upgrade to edgy
UUID=42B4-13B5 /media/shared vfat iocharset=utf8,umask=000 0 0
# /dev/hda2 -- converted during upgrade to edgy
UUID=6CA4C4FFA4C4CD30 /media/windows ntfs-3g defaults,locale=en_US.utf8 0 0
# /dev/hda5 -- converted during upgrade to edgy
#UUID=0660dd36-97cf-40c0-9321-5c88da58132c none swap sw 0 0
/dev/hda5 none swap sw 0 0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
```

as you can see ive tried commenting out the line created by the upgrade and changing it back to the old style, and that didnt fix the problem.

```
sudo swapon -a
```
gives
```
swapon: /dev/hda5: Invalid argument
```

also, im not sure if its related, but if i go to system settings, then disks and filesystems, and go into administrator mode, it says that the module could not be loaded, it lists possible reasons as 3rd party modules or error during upgrade.

ive searched all over the forums and google for fstab issues, and havent been able to figure out why my swap is not working.  i do not notice any significant difference in performance for not having swap, and i could not confidently say that swap was on before i upgraded to dapper.

thanks in advance for the help
-ryan

---

### Post by taurus on 2006-12-24
What's the output of this command from a terminal?

```
sudo fdisk -l
```

---

### Post by meng on 2006-12-24
I wonder what would happen if you commented the second-last line (/dev/hda5) and UNcommented the line above it.

---

### Post by ryan00davis on 2006-12-24
```
ryan@ryan-laptop:~$ sudo fdisk -l

Disk /dev/hda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1           5       40131    6  FAT16
/dev/hda2   *           6        2027    16241715    7  HPFS/NTFS
/dev/hda3            2028        6265    34041735    c  W95 FAT32 (LBA)
/dev/hda4            6266        7296     8281507+   5  Extended
/dev/hda5            6266        6380      923706   82  Linux swap / Solaris
/dev/hda6            6381        7296     7357738+  83  Linux

```


as for the fstab suggestion:
and i origionally had it left as the line above it (the automatically generated line during upgrade), it didnt work, thats when i decided to switch to the other style for fstab (the style i kinda understand) and that didnt work either.

---

### Post by taurus on 2006-12-24
```
sudo mkswap /dev/hda5
sudo swapon /dev/hda5
free
```

---

### Post by ryan00davis on 2006-12-24
that seemed to fix it.
im not sure why i didnt think of mkswap (i did semi-successfully install gentoo once, haha).
anyways, thanks a lot for the help, especially the speed of the reply.

have a marry x-mas (or any other holliday you celebrate) tomorrow.
-ryan

---

### Post by Trymic on 2007-01-01
I followed Taurus instruction and fixed the problem
Well done Taurus

---

### Post by taurus on 2007-01-01
> **Trymic said:**
> I followed Taurus instruction and fixed the problem
Well done Taurus

Oh me!!!

---

### Post by Pylg on 2007-01-05
Hi all, I'm using Ubuntu 6.10 for a few month. I got exactly the same problem. A free shows me that swap is empty. Doing the previous operation, my swap begins to be useful (I tested it opening everything possible..)

HOWEVER, afrer a reboot, all is lost. Problem appears again and the makeswap-swapon has to be done again.

Does someone have something to avoid doing it at each reboot ? Thanks !!!

PS : is it a known bug of this Ubuntu version (6.10) ?

---

### Post by taurus on 2007-01-05
What does your /etc/fstab look like?

Applications -> Accessories -> Terminal
```
cat /etc/fstab
```
And might as well include the output of this command too.

```
sudo fdisk -l
```

---

### Post by Pylg on 2007-01-06
Hello Taurus, thanks for your response. My fstab gives :

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda10 -- converted during upgrade to edgy
UUID=bc7743da-57be-47c8-930d-42a390527f2d / ext3 defaults,errors=remount-ro 0 1
#/dev/sda1       /media/sda1     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda12 -- converted during upgrade to edgy
UUID=c484d9ba-8ec1-4bb6-9615-abc3bfc1f04f /home ext3 defaults 0 2
# /dev/sda2 -- converted during upgrade to edgy
UUID=320D-180E /media/sda2 vfat defaults,utf8,umask=007,gid=46 0 1
# /dev/sda5 -- converted during upgrade to edgy
UUID=44F4-B041 /media/sda5 vfat defaults,utf8,umask=007,gid=46 0 1
# /dev/sda6 -- converted during upgrade to edgy
UUID=89E9-6106 /media/sda6 vfat defaults,utf8,umask=007,gid=46 0 1
# /dev/sda7 -- converted during upgrade to edgy
UUID=CEDE-1195 /media/sda7 vfat defaults,utf8,umask=007,gid=46 0 1
# /dev/sda8 -- converted during upgrade to edgy
UUID=9c898b62-b60d-455a-9e5b-00e9b9abf5fc /media/sda8 ext3 defaults 0 2
# /dev/sda9 -- converted during upgrade to edgy
UUID=ca74a5c0-a4a3-4f57-a46e-dcb9f04eace0 /media/sda9 ext3 defaults 0 2
# /dev/sda11 -- converted during upgrade to edgy
UUID=bd041f06-556a-4418-aa95-e268b88cb8af none swap sw 0 0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

The fdisk :

Disque /dev/sda: 250.0 Go, 250059350016 octets
255 têtes, 63 secteurs/piste, 30401 cylindres
Unités = cylindres de 16065 * 512 = 8225280 octets

Périphérique Amorce    Début         Fin      Blocs    Id  Système
/dev/sda1               1         637     5116671   12  Compaq diagnostics
/dev/sda2   *         638        5736    40957717+   c  W95 FAT32 (LBA)
/dev/sda3            5737       30401   198121612+   f  W95 Etendu (LBA)
/dev/sda5            5737       10836    40965718+   b  W95 FAT32
/dev/sda6           18487       23586    40965718+   b  W95 FAT32
/dev/sda7           23587       30401    54741456    b  W95 FAT32
/dev/sda8           15937       17211    10241406   83  Linux
/dev/sda9           17212       18486    10241406   83  Linux
/dev/sda10          10837       13386    20482843+  83  Linux
/dev/sda11          13387       13641     2048256   82  Linux swap / Solaris
/dev/sda12          13642       15936    18434556   83  Linux

Les entrées de la table de partitions ne sont pas dans l'ordre du disque

I found two interesting links yesterday about the same problem (I hope !). Here they are :

[https://launchpad.net/ubuntu/+bug/66637](https://launchpad.net/ubuntu/+bug/66637)

[https://launchpad.net/ubuntu/+bug/72016](https://launchpad.net/ubuntu/+bug/72016)

Thanks for your help.

PY

---

### Post by Pylg on 2007-01-06
Modifying my fstab like that 

# /dev/sda11 -- converted during upgrade to edgy
#UUID=bd041f06-556a-4418-aa95-e268b88cb8af none swap sw 0 0
/dev/sda11      none            swap    sw              0       0

now it works even after several reboot ! free gives something correct :

# /dev/sda11 -- converted during upgrade to edgy
#UUID=bd041f06-556a-4418-aa95-e268b88cb8af none swap sw 0 0
/dev/sda11      none            swap    sw              0       0

However, it may be not as clean as what other Ubuntu users did (see my previous link). Shouls I keeep it like that or should I alos upadate conf.d and initrd ... ??? Thanks

---

### Post by gardara on 2007-01-06
> **Pylg said:**
> I got exactly the same problem. A free shows me that swap is empty. Doing the previous operation, my swap begins to be useful (I tested it opening everything possible..)

HOWEVER, afrer a reboot, all is lost. Problem appears again and the makeswap-swapon has to be done again.

Does someone have something to avoid doing it at each reboot ? Thanks !!!


I also have the same problem. 

my /etc/fstab looks like this:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2 -- converted during upgrade to edgy
UUID=87a30623-c163-477c-a28d-5cc101a526e5 / ext3 defaults,errors=remount-ro 0 1
# /dev/sda4 -- converted during upgrade to edgy
UUID=e2ab997f-c60a-4a45-8c48-5482f1c74541 /home ext3 defaults 0 2
# /dev/sda1 -- converted during upgrade to edgy
UUID=3A48AB4E48AB07A9 /windows ntfs defaults,nls=utf8,umask=007,gid=46 0 1
# /dev/sda3 -- converted during upgrade to edgy
UUID=0fbfcddb-c2bb-465c-8c05-d0c5043377e2 none swap sw 0 0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0

```

and sudo fdisk -l gives me
```
Disk /dev/sda: 58.5 GB, 58506416640 bytes
255 heads, 63 sectors/track, 7113 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1912    15358108+   7  HPFS/NTFS
/dev/sda2            1913        3824    15358140   83  Linux
/dev/sda3            3825        4079     2048287+  82  Linux swap / Solaris
/dev/sda4            4080        7113    24370605   83  Linux
 
```

Can you help me taurus? or anyone else? :)

Thanks in advance

---

### Post by taurus on 2007-01-06
Okay, edit your /etc/fstab with

Applications -> Accessories -> Terminal
```
gksudo gedit /etc/fstab
```
and replace this line
```
UUID=0fbfcddb-c2bb-465c-8c05-d0c5043377e2 none swap sw 0 0
```
with this line.
```
/dev/sda3   none   swap   sw   0   0
```
Save it and see if you can mount it now.

```
sudo mount -a
free
```

---

### Post by gardara on 2007-01-06
that seems to have fixed it :)

Thank you so much!

...Now let's hope [hibernation will work now](http://ubuntuforums.org/showthread.php?p=1974204)

:D

---

### Post by gardara on 2007-01-06
I just tried hibernating, when I did that I got this message "17179948.94800 hda_intel azx_get_response timeout switching to single_cmd mode"
And when I turned my laptop back on then it's like I was booting it after a restart. and now my swap is gone "free" gives me

```
Swap:            0          0          0

```

the swap was still there after a normal reboot I did earlier, but now after I tried hibernating it's all gone ](*,)

---

### Post by taurus on 2007-01-06
What does your /etc/fstab look again?

```
cat /etc/fstab
```

---

### Post by gardara on 2007-01-06
it looks like this now:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2 -- converted during upgrade to edgy
UUID=87a30623-c163-477c-a28d-5cc101a526e5 / ext3 defaults,errors=remount-ro 0 1
# /dev/sda4 -- converted during upgrade to edgy
UUID=e2ab997f-c60a-4a45-8c48-5482f1c74541 /home ext3 defaults 0 2
# /dev/sda1 -- converted during upgrade to edgy
UUID=3A48AB4E48AB07A9 /windows ntfs defaults,nls=utf8,umask=007,gid=46 0 1
# /dev/sda3 -- converted during upgrade to edgy
/dev/sda3   none   swap   sw   0   0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0

```

---

### Post by taurus on 2007-01-06
What's the output of the last command from a terminal?

```
sudo mount -a
free
```

---

### Post by gardara on 2007-01-06
```
gardar@glappi:~$ sudo mount -a
Password:
gardar@glappi:~$ free
             total       used       free     shared    buffers     cached
Mem:       1026328     500512     525816          0      25544     217220
-/+ buffers/cache:     257748     768580
Swap:            0          0          0

```

---

### Post by taurus on 2007-01-06
Try

```
sudo mkswap /dev/sda3
sudo swapon /dev/sda3
free
```

---

### Post by gardara on 2007-01-06
```
gardar@glappi:~$ sudo mkswap /dev/sda3
Setting up swapspace version 1, size = 2097438 kB
no label, UUID=73c86314-57de-4c4d-9376-d7b53ec79005
gardar@glappi:~$ sudo swapon /dev/sda3
gardar@glappi:~$ free
             total       used       free     shared    buffers     cached
Mem:       1026328     502836     523492          0      26796     217296
-/+ buffers/cache:     258744     767584
Swap:      2048276          0    2048276

```

now let's see if this keeps the same after a reboot and a hibernate.

---

### Post by gardara on 2007-01-06
ok I did a reboot, everything seemed fine, the swap was still there.
Then I tried to hibernate. The computer didn't hibernate, because when I started my laptop again there didn't anything resume like it's supposed to be when hibernating, the folders and stuff I had open were closed all, so it was more like I had just turned the laptop off and then on again. Except for that the swap is gone. Free looks like this after the hibernate:

```
             total       used       free     shared    buffers     cached
Mem:       1026328     491372     534956          0      21648     216488
-/+ buffers/cache:     253236     773092
Swap:            0          0          0

```

---

### Post by taurus on 2007-01-06
Looks like the hibernation process just kills your swap!!!  ](*,)

---

### Post by gardara on 2007-01-06
yeah, you have any idea what can be wrong?

maby this error message I sometimes get when trying to hibernate has something to do with it? 
```
17179948.94800 hda_intel azx_get_response timeout switching to single_cmd mode
```

Myself, I have no idea what this error message means..

---

### Post by taurus on 2007-01-06
I don't use hibernate so I am not sure what is the correct way to get it to work.  Sorry...

---

### Post by gardara on 2007-01-06
allright, well I'll just go back to my hibernation thread and hope someone will be able to help me [http://ubuntuforums.org/showthread.php?p=1974204](http://ubuntuforums.org/showthread.php?p=1974204)

But thanks for your great help :)

---

