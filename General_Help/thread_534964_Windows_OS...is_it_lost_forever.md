---
title: "Windows OS...is it lost forever"
date: 2007-08-25
forum: General Help
---

### Post by Kevin J on 2007-08-25
I recently downloaded Ubuntu 7.04 onto a new XPS 210 dell.
I did not realize that I would not (easily) be able to switch from Ubuntu to Windows. I assumed (wrongly) that when booting I would be given the choice.
Can anyone tell me how to boot to the Windows OS as well as the Ubuntu?
I am not familiar with acronyms and numbers that surround these problems, but.......if more information is needed I can supply it. (I can still just about read and write, if not comprehend.)

Kevin J

---

### Post by williamwade on 2007-08-25
Did you install it on the same partition as xp?

---

### Post by oilchangeguy on 2007-08-25
> **Kevin J said:**
> I recently downloaded Ubuntu 7.04 onto a new XPS 210 dell.
I did not realize that I would not (easily) be able to switch from Ubuntu to Windows. I assumed (wrongly) that when booting I would be given the choice.
Can anyone tell me how to boot to the Windows OS as well as the Ubuntu?
I am not familiar with acronyms and numbers that surround these problems, but.......if more information is needed I can supply it. (I can still just about read and write, if not comprehend.)

Kevin J

when you installed ubuntu, did you by chance allow it to use the entire drive?

---

### Post by merlinus on 2007-08-25
Do you see a grub menu on startup?  If so, what options are offered?

Whilst in ubuntu, open a terminal (Applications/Accessories) and enter these commands one at a time, and post the results:

```

sudo fdisk -l
cat /boot/grub/menu.lst
cat /etc/fstab

```

-merlin

---

### Post by gletob on 2007-08-25
please tell me you didnt use WUBI that is the most evil piece of software ever
but if you are using GRUB in ubuntu try  sudo update-grub

---

### Post by Kevin J on 2007-08-26
Melinus,
I do not see the menu on start up. It does flash "grub menu loading"
I have opened a command menu (it asks if I am an administrator, I guess I am)
I see my user name and the name I gave to the computer when installing.
I have entered the following commands 
sudo fdisk -1
pressed enter
asks for password.
Large flashing cursor appears 
Screen will not type the password.

Am I going backwards here?

Thanks for the responses I really do need the help

KevinJ

---

### Post by freebeer on 2007-08-26
when prompted for a password... just type it and hit the enter key.  The password characters are not echoed to the screen.  (security reasons)  This is normal.

---

### Post by Kevin J on 2007-08-26
Merlinus,
this is a copy of the screen I get when I type the following into terminal.
kevin@kevin-desktop:(wavy line, that I cannot find on my keyboard.)-$ sudo fisk-1
sudo: fdisk-1: command not found
kevin@kevin-desktop: (wavy line I cannot find on my keyboard)-$ sudo fdisk -1
fdisk: invalid option --1

Usage: fdisk [-b SSZ] [-u] DISK     Change partition table
            fdisk - (Wavy 'connector' look alike symbol that I cannot find) [-b SSZ] Disk  list partition table (s)
            fdisk - PARTITION                                                                                           give partition size (s)
            fdisk -v                               Give fdisk version
Here DISK  is something like /dev/hdb/ or /dev/sda
and PARTITION is something like /dev/hda7
-u: give Start and End in sector (instead of cylinder) units
-b 2048 (for certain MO disks) use 2048-byte sectors


I then ran the command fdisk -s  PARTITION

AND:
unable to open PARTITION 

Came up.


Hope this accurate enough to be going along with. 
On a very steep learning curve here 


Kevin J

---

### Post by Irony on 2007-08-26
Copy and paste the following;

[PHP]sudo fdisk -l[/PHP]

You typed sudo fdisk -1 which won't work.

Note; to copy and paste highlight the above then middle click in your terminal.

---

### Post by freebeer on 2007-08-26
it's not a "1" but a lowercase L.

```

sudo fdisk -l

```

For ease of simplicity and to decrease typos, it's best to just copy and paste commands that you're unfamiliar with.  To paste in the terminal window use SHIFT-INSERT.

---

### Post by Kevin J on 2007-08-26
I managed to copy and paste the screen through open office.
so this is a screen shot.



kevin@kevin-desktop:~$ sudo fdisk-1 
sudo: fdisk-1: command not found 
kevin@kevin-desktop:~$ sudo fdisk -1 
fdisk: invalid option -- 1 

Usage: fdisk [-b SSZ] [-u] DISK     Change partition table 
       fdisk -l [-b SSZ] [-u] DISK  List partition table(s) 
       fdisk -s PARTITION           Give partition size(s) in blocks 
       fdisk -v                     Give fdisk version 
Here DISK is something like /dev/hdb or /dev/sda 
and PARTITION is something like /dev/hda7 
-u: give Start and End in sector (instead of cylinder) units 
-b 2048: (for certain MO disks) use 2048-byte sectors 
kevin@kevin-desktop:~$ 
kevin@kevin-desktop:~$ fdisk -s PARTITION 

Unable to open PARTITION 
kevin@kevin-desktop:~$

---

### Post by hessiess on 2007-08-26
boot the live cd, open up gperted (system, administration, gparted) it should list more than 2 partitions. outherwise you wiped the disk

---

### Post by khughitt on 2007-08-26
you may have to use the command:
```
sudo /sbin/fdisk -l
```

---

### Post by lgcabarcas on 2007-08-26
> **Kevin J said:**
> I managed to copy and paste the screen through open office.
so this is a screen shot.



kevin@kevin-desktop:~$ sudo fdisk-1 
sudo: fdisk-1: command not found 
kevin@kevin-desktop:~$ sudo fdisk -1 
fdisk: invalid option -- 1 

Usage: fdisk [-b SSZ] [-u] DISK     Change partition table 
       fdisk -l [-b SSZ] [-u] DISK  List partition table(s) 
       fdisk -s PARTITION           Give partition size(s) in blocks 
       fdisk -v                     Give fdisk version 
Here DISK is something like /dev/hdb or /dev/sda 
and PARTITION is something like /dev/hda7 
-u: give Start and End in sector (instead of cylinder) units 
-b 2048: (for certain MO disks) use 2048-byte sectors 
kevin@kevin-desktop:~$ 
kevin@kevin-desktop:~$ fdisk -s PARTITION 

Unable to open PARTITION 
kevin@kevin-desktop:~$

what' been messing you up is that you type:
sudo fdisk-1 

-two problems first: the last character it's a lower case l NOT A 1, letter not number, and also you must set a space between the command fdisk and the option -l [fdisk -l]

---

### Post by Kevin J on 2007-08-26
this is the result of typing lower case l instead of 1.
I noted some 'curvy' lines on the text in ubuntu, which corresponds to the lower case L.
Hiope this helps


Kevin J



kevin@kevin-desktop:~$ sudo fdisk -l 
Password: 

Disk /dev/sda: 250.0 GB, 250000000000 bytes 
255 heads, 63 sectors/track, 30394 cylinders 
Units = cylinders of 16065 * 512 = 8225280 bytes 

   Device Boot      Start         End      Blocks   Id  System 
/dev/sda1   *           1       29641   238091301   83  Linux 
/dev/sda2           29642       30394     6048472+   5  Extended 
/dev/sda5           29642       30394     6048441   82  Linux swap / Solaris 

Disk /dev/sdb: 4127 MB, 4127194624 bytes 
255 heads, 63 sectors/track, 501 cylinders 
Units = cylinders of 16065 * 512 = 8225280 bytes 

   Device Boot      Start         End      Blocks   Id  System 
/dev/sdb1   *           1         502     4030432    6  FAT16 
Partition 1 has different physical/logical endings: 
     phys=(500, 254, 63) logical=(501, 196, 14) 
kevin@kevin-desktop:~$

---

### Post by aldenhg on 2007-08-26
It looks like you messed up when installing Ubuntu and nuked your Windows installation. Unless you want to pay to have a computer tech try and recover it (which probably won't work anyway) you're more or less hosed. This is why you should always back up before you do anything as major as installing another OS.

---

### Post by Kevin J on 2007-08-26
If the windows is lost....
Dell gave me a re-installation CD for window vista.
I tried to run the cd whilst using ubuntu 7.04 but was told no program existed to read the application.
Is there a way to use the reinstallation dvd to get windows back?

what should I do to re-install?

kevin J

---

### Post by merlinus on 2007-08-26
I would think you have to boot from the cd.

-merlin

---

### Post by Roaster on 2007-08-26
You must reformat the disk for Windows to "see" it. Clean install of Vista and then dual boot Ubuntu if you just have to have Windows. Install will format the disk, best of luck.

---

### Post by Spr0k3t on 2007-08-27
The restore disc for Vista will wipe your Ubuntu installation clean... so you will need reinstall Ubuntu once Vista install is done.

---

### Post by MustNotSleep on 2007-08-27
yikes! i feel bad for you..

this is why you should always investigate and read up prior to doing something you're not sure about. there are plenty of installation guides for Ubuntu out there that take you step by step through the process.

here's one: [http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

read up, get familiar with the concepts, always have a plan B if something goes wrong (backup!), etc.. and once you're done installing, get used to reading some more and spend precious time fiddling around with the system to get it working just the way you want it (and hosing a few installs on the way)..

good luck!

---

### Post by khughitt on 2007-08-27
An easy way to set-up a dual boot with Windows XP and Ubuntu is to set-up your disk partitions how you want them before installing anything. Then install windows XP, and specify that it should only use the partition you created for it, and not the entire hard-drive. Finally, install ubuntu and similarly specify that it should only use the partition(s) you provided for it, and not the entire drive.

Partitions can be a tricky to get the hang of at first, but it helps to understand how they work. Once you understand [a little bit about disk partitions]("http://www.pcguide.com/ref/hdd/file/structPartitions-c.html") they are not that hard to manipulate.

If you are not sure of how you should go about partitioning your drive before trying to install again, just ask :)

---

### Post by Kevin J on 2007-08-27
Thanks to everyone, Especially Merlinus.
I have bookmarked some sites on creating partitions. I will also go to the library and find myself Linux for Dummies.
I will try the re-install after I feel a little more confident. I am sure there will be more questions later

thanks evryone

kevin J

---

