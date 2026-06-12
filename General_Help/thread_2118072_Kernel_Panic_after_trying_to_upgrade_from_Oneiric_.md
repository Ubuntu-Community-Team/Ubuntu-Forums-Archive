---
title: "Kernel Panic after trying to upgrade from Oneiric to Precise"
date: 2013-02-20
forum: General Help
---

### Post by edwardandtubs on 2013-02-20
As the title says, I've got a kernel panic and cannot boot my machine at all. This has happened after trying to upgrade to Precise. 

I've tried all the recovery modes in GRUB to no avail, I have noticed that the GRUB lists Ubuntu 11.10 tho and not 12.04

I've attached a screen pic of whats happening.

Any advice/help would be greatly appreciated as this is my main server.

---

### Post by fuorviatos on 2013-02-20
Have you tried booting with a different kernel?
If you have, I'd try to boot up a live version and chroot to the system so we can have a deeper look on some log files.

---

### Post by edwardandtubs on 2013-02-20
> **fuorviatos said:**
> Have you tried booting with a different kernel?
If you have, I'd try to boot up a live version and chroot to the system so we can have a deeper look on some log files.

I've tried the other kernels and get the same. 

I'll get the live version booted and use chroot

---

### Post by fuorviatos on 2013-02-20
I'm not on my Ubunto box now as I'm at work where Windows is used so I don't really remember the commands. Meanwhile, you could try to boot up the live version, open up a terminal session and type (If I remember well):

> sudo apt-get install chrootAfter the installation, I would issue this command

> mount|grep sda* (assuming you've got only one hard drive)

Then you'll need to find out where your Ubuntu partition is .
Let's assume for me it is on /dev/sda1 so what I'd do is:

> sudo suthen
> mkdir /media/Ubuntuthen
> mount -t ext3 /dev/sda1 /media/Ubuntuthen
> chroot /media/Ubuntuthen 
> cd /var/log/If you came across all those steps, you'll find yourself in the directory that stores all of your Ubuntu installation logs.
Tell us when you do, so we can start to investigate your issue

---

### Post by edwardandtubs on 2013-02-20
Seems that chroot is already installed. 

Anyhow I've mounted the boot disk (sda1) as /media/Ubuntu

When I try to chroot I get the following error (which is the same as in the kernel panic )

> root@ubuntu:~# chroot /media/Ubuntu
/bin/bash: error while loading shared libraries: libjpeg.so.8: cannot open shared object file: No such file or directory


If I then cd to /var/log, this is the livecd directory. I`ve confirmed this by cd to /media/Ubuntu/var/log and making sure the contents are different.

So it seems as if I can't even chroot to the disk to try and start fixing it:(

---

### Post by fuorviatos on 2013-02-20
As far as I can get it, your system is missing some important libraries. Maybe we can try to find out what package contains it. Try:

1.> sudo apt-get install apt-file2. > apt-file update3. > apt-file search libjpeg.so.8This should tell us where to get the library from.

---

### Post by edwardandtubs on 2013-02-20
Seems as if the LIVE version won't let me do that even tho I've enabled the universe software source.

> ubuntu@ubuntu:~$ sudo apt-get install apt-file
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package apt-file
ubuntu@ubuntu:~$ apt-file
The program 'apt-file' is currently not installed. You can install it by typing:
sudo apt-get install apt-file


---

### Post by dino99 on 2013-02-20
you should do a fresh install (huge changes exist between OO & PP)

[http://ubuntuforums.org/showpost.php?p=12495221&postcount=2](http://ubuntuforums.org/showpost.php?p=12495221&postcount=2)

---

### Post by fuorviatos on 2013-02-20
Check with >  ping -c 5 [www.google.com](www.google.com) to make sure you're connected to the internet.

---

### Post by edwardandtubs on 2013-02-20
> **fuorviatos said:**
> Check with  to make sure you're connected to the internet.

I definately am connected as I'm writing on here using Firefox on the live cd :D

---

### Post by fuorviatos on 2013-02-20
OK, dino99's idea of a fresh install is obviously a good idea, but if you want to play a bit, maybe we can get to understand what has broken your system ;).
Show us your apt sources file please

---

### Post by edwardandtubs on 2013-02-20
I've been meaning to do a fresh install for a while however was worried about getting back at my LVM disks however I can see them using the LIVE cd so hopefully they'll mount on a fresh install

Attached is sources.list

That said, I'd like to play about a bit and see if I can get this working... as its serves my house with media (via Raspbmc), has Zoneminder all setup and working correctly, setup as my download server, sync's my icloud photos (using virtual machine and Windows 7) and has backups running to a usb drive (its used quite a bit!)

---

### Post by fuorviatos on 2013-02-20
OK, and what does this  say ?

> sudo lsb_release -a

Next thing; let's try to install directly the package containing the missing library

> sudo apt-get install [libjpeg-turbo8]("http://packages.ubuntu.com/precise/libjpeg-turbo8") 

Any progress?

---

### Post by edwardandtubs on 2013-02-20
> **fuorviatos said:**
> OK, and what does this  say ?



Next thing; let's try to install directly the package containing the missing library



Any progress?

It'd be great to do that but I can't chroot onto the disk itself

---

### Post by fuorviatos on 2013-02-20
> **edwardandtubs said:**
> It'd be great to do that but I can't chroot onto the disk itself
Yeah, sure, but still I'm not sure if it's chroot command complaining about the library or just you system which is corrupt , so I need to restrain to only one option.

---

### Post by edwardandtubs on 2013-02-20
> root@ubuntu:/home/ubuntu# chroot /media/Ubuntu/
/bin/bash: error while loading shared libraries: libjpeg.so.8: cannot open shared object file: No such file or directory
root@ubuntu:/home/ubuntu# sudo lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 12.10
Release:	12.10
Codename:	quantal
root@ubuntu:/home/ubuntu# sudo apt-get install libjpeg-turbo8
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libjpeg-turbo8 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
root@ubuntu:/home/ubuntu#


ok, tried it...

---

### Post by fuorviatos on 2013-02-20
Still wanna play ;) ?
If so, attach your > /etc/ld.so.conffile

EDIT: Also become root and do 
> locate libjpeg.so.8 because we need to know the path to the library.

---

### Post by edwardandtubs on 2013-02-20
Ok before I read your last post I located the libjpeg.so.8 file on the live system and copied it to /usr/lib/i386-linux-gnu on my main disk. 

I was then able to chroot onto the main disk, albeit with some errors 


> 
ubuntu@ubuntu:~$ sudo lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 12.10
Release:	12.10
Codename:	quantal
ubuntu@ubuntu:~$ sudo chroot /media/Ubuntu/
Error opening file for reading: No such file or directory
Error opening file for reading: No such file or directory
root@ubuntu:/# lsb_release -a
Error opening file for reading: No such file or directory
Error opening file for reading: No such file or directory
LSB Version:	core-2.0-ia32:core-2.0-noarch:core-3.0-ia32:core-3.0-noarch:core-3.1-ia32:core-3.1-noarch:core-3.2-ia32:core-3.2-noarch:core-4.0-ia32:core-4.0-noarch:cxx-3.0-ia32:cxx-3.0-noarch:cxx-3.1-ia32:cxx-3.1-noarch:cxx-3.2-ia32:cxx-3.2-noarch:cxx-4.0-ia32:cxx-4.0-noarch:desktop-3.1-ia32:desktop-3.1-noarch:desktop-3.2-ia32:desktop-3.2-noarch:desktop-4.0-ia32:desktop-4.0-noarch:graphics-2.0-ia32:graphics-2.0-noarch:graphics-3.0-ia32:graphics-3.0-noarch:graphics-3.1-ia32:graphics-3.1-noarch:graphics-3.2-ia32:graphics-3.2-noarch:graphics-4.0-ia32:graphics-4.0-noarch:printing-3.2-ia32:printing-3.2-noarch:printing-4.0-ia32:printing-4.0-noarch:qt4-3.1-ia32:qt4-3.1-noarch
Distributor ID:	Ubuntu
Description:	Ubuntu 12.04.2 LTS
Release:	12.04
Codename:	precise


I tried rebooting and whilst I now get a login prompt if I login and try and run 'startx' I get an error about nvidia not being able to find a display. 

So, now I've got chroot whats best to try first??

---

### Post by fuorviatos on 2013-02-20
Show me your Xorg.0 log (grep for (EE) records to get the most relevant info)

---

### Post by edwardandtubs on 2013-02-20
> [   266.785] (II) Loading extension MIT-SCREEN-SAVER
[   266.829] (EE) NVIDIA: Failed to load the NVIDIA kernel module. Please check your
[   266.830] (EE) NVIDIA:     system's kernel log for additional error messages.
[   266.830] (EE) Failed to load module "nvidia" (module-specific error, 0)
[   266.830] (EE) No drivers available.

I've tried installing nvidia-common and its says its installed??

---

### Post by fuorviatos on 2013-02-20
I need to go now. Please, try to remove everything related to the nvidia drivers, then backup your Xorg.conf and remove it too.
It should get recreated automatically with the nouveau driver on startup.
Let us know if that helps

---

### Post by edwardandtubs on 2013-02-20
> **fuorviatos said:**
> I need to go now. Please, try to remove everything related to the nvidia drivers, then backup your Xorg.conf and remove it too.
It should get recreated automatically with the nouveau driver on startup.
Let us know if that helps

thanks...I'm trying that at the moment. I'll report back

---

### Post by edwardandtubs on 2013-02-20
Well removing the nvidia drivers and rebooting seems to have partially fixed it, I've got a desktop back and that - however!, if I boot into gnome classic, the top and bottom menu bars have disappeared, and if I boot into ubuntu 3d, some of the colours seem wrong in some windows (white text on grey background). 

Not sure what to try next?

---

### Post by fuorviatos on 2013-02-21
First of all, backup your data as your system is only partially recovered :)

What I would go for from now is:

1. Make sure everything related to nvidia has been removed from the system (especially, nvidia-kernel modules) so, as root

> dpkg -l|grep 'nvidia'  

it shouldn't give you any results with the [ii] mark.

2. Browse your Xorg.0.log to find out if anything messy happens to the driver 

3. Try to create a new user account and check if the distortion persists in that condition as well.

---

### Post by edwardandtubs on 2013-02-21
I persisted with this last night and got nvidia removed. I then noticed that when logging on in Terminal it mentioned I had X number of packages to update. 

I ran sudo apt-get update and it didnt do anything, so then I ran sudo apt-get dist-upgrade. It seems it had only partially updated the distribution. I got some errors and had to resort back to the Live CD in order to chroot and fix but I'm now back up and running again. I'm sure under the covers its not totally fixed but I can live with it until I get chance to do a fresh install.

Thanks for your help again, much appreciated.

---

### Post by fuorviatos on 2013-02-21
> **edwardandtubs said:**
> I persisted with this last night and got nvidia removed. I then noticed that when logging on in Terminal it mentioned I had X number of packages to update. 

I ran sudo apt-get update and it didnt do anything, so then I ran sudo apt-get dist-upgrade. It seems it had only partially updated the distribution. I got some errors and had to resort back to the Live CD in order to chroot and fix but I'm now back up and running again. I'm sure under the covers its not totally fixed but I can live with it until I get chance to do a fresh install.

Thanks for your help again, much appreciated.
OK. If that's it for you, please mark the thread as (SOLVED)

Cheers :)

---

