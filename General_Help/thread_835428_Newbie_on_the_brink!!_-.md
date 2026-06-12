---
title: "Newbie on the brink!! -"
date: 2008-06-20
forum: General Help
---

### Post by TheRealYeti on 2008-06-20
I'm a new user to Ubuntu after 15 + years of a Windows only environment and loving it.  Apart from the fact that I seem to have screwed up my installation already.

I'm not really sure how I've done it but currently my system won't boot and stops a this point;

*Setting kernel variables...       [ok]
.: 17: Can't open /lib/init/vars.sh
.: 24: Can't open /lib/init/mount-function.sh
.: 16: Can't open /lib/init/vars.sh
.: 15: Can't open /lib/init/vars.sh
.: 11: Can't open /lib/init/vars.sh
* Checking minimum space in /tmp...          [ok]
mv:  inter-device move failed: '/dev/.udev.log' to '/var/log/udev' ; unable to remove target: read-only file system
/etc/rcS.d/S39readhead-desktop: 73: mountpoint: not found
/etc/rcS.d/S39readhead-desktop: 73: mountpoint: not found
* Skipping firewall: ufw (not enabled)...          [ok]
* Configuring network interfaces...                 [fail]
/etc/rcS.d/S45waitnfs.sh: 106: /lib/init/mountall-net-fs: not found
.: 11: Can't open /lib/init/vars.sh
chmod: changing permissions of '/var/run/screen':  Read-only file system
chown: changing ownership of '/tmp/.X11-unix': Read-only file system
.: 14: Can't open /lib/init/vars.sh
.: 19: Can't open /lib/init/vars.sh
init: rc-default main process (4636) terminated with status 127

It look like i must have changed some ownership of some critical directories my mistake.

Does anyone have some suggestion on how to save this installation ?

Please don't make me go back to windows!:lolflag:

---

### Post by dracayr on 2008-06-20
execute the following commands in a terminal:

```
ls -l /lib/init/
ls -ld /lib/init
ls -ld /lib
```

post the output

dracayr

---

### Post by jimv on 2008-06-20
> **dracayr said:**
> execute the following commands in a terminal:

```
ls -l /lib/init/
ls -ld /lib/init
ls -ld /lib
```

post the output

dracayr

BTW, since you can't boot your computer normally, you'll have to do these commands from the LiveCD.  (Make sure you run the commands on the /lib folder for your ubuntu install instead of the /lib folder on the cd.  The one for your Ubuntu install will be something like /media/hda0/lib/.....

---

### Post by dracayr on 2008-06-20
> **jimv said:**
> BTW, since you can't boot your computer normally, you'll have to do these commands from the LiveCD.  (Make sure you run the commands on the /lib folder for your ubuntu install instead of the /lib folder on the cd.  The one for your Ubuntu install will be something like /media/hda0/lib/..... yeah, forgot to mention that. Also, have you tried the recovery mode?

dracayr

---

### Post by TheRealYeti on 2008-06-20
ubuntu@ubuntu:/media/disk/lib$ ls -l /lib/init/
total 24
-rwxr-xr-x 1 root root  2702 2008-04-18 16:02 mountall-net-fs
-rw-r--r-- 1 root root  3094 2008-04-18 16:02 mount-functions.sh
-rwxr-xr-x 1 root root 11224 2008-04-18 16:02 readlink
-rw-r--r-- 1 root root  5630 2008-04-18 16:02 usplash-fsck-functions.sh
-rw-r--r-- 1 root root   129 2008-04-18 16:02 vars.sh

ubuntu@ubuntu:/media/disk/lib$ ls -ld /lib/init
drwxr-xr-x 2 root root 110 2008-04-22 18:02 /lib/init

ubuntu@ubuntu:/media/disk/lib$ ls -ld /lib
drwxr-xr-x 17 root root 60 2008-06-20 17:39 /lib

I think I've done this right!

---

### Post by TheRealYeti on 2008-06-20
If you mean recovery mode as in the second option on the GRUB menu then yes but I get the same result.

---

### Post by jimv on 2008-06-20
Try running fsck from the live cd on your Ubuntu partition.

sudo fsck -pyv hda1 (or whatever your ubuntu partition is)

---

### Post by dracayr on 2008-06-20
> **TheRealYeti said:**
> ubuntu@ubuntu:/media/disk/lib$ ls -l /lib/init/
total 24
-rwxr-xr-x 1 root root  2702 2008-04-18 16:02 mountall-net-fs
-rw-r--r-- 1 root root  3094 2008-04-18 16:02 mount-functions.sh
-rwxr-xr-x 1 root root 11224 2008-04-18 16:02 readlink
-rw-r--r-- 1 root root  5630 2008-04-18 16:02 usplash-fsck-functions.sh
-rw-r--r-- 1 root root   129 2008-04-18 16:02 vars.sh

ubuntu@ubuntu:/media/disk/lib$ ls -ld /lib/init
drwxr-xr-x 2 root root 110 2008-04-22 18:02 /lib/init

ubuntu@ubuntu:/media/disk/lib$ ls -ld /lib
drwxr-xr-x 17 root root 60 2008-06-20 17:39 /lib

I think I've done this right!

no, you haven't. when you're in that directory, simply execute the commands
```
ls -l init/
ls -ld init
 ls -ld .
```
alternatively, execute the commands 
```
ls -l /media/disk/lib/init/
ls -ld /media/disk/lib/init/
 ls -ld /media/disk/lib
```

dracayr

---

### Post by VMC on 2008-06-20
I'm curious.When you installed ubuntu, did it work the first time? If so, do you know exactly what you did after that.

---

### Post by TheRealYeti on 2008-06-20
fsck 1.40.8 (13-Mar-2008)
e2fsck 1.40.8 (13-Mar-2008)
/dev/sdd5: clean, 178041/3096576 files, 4137652/12357993 blocks

---

### Post by TheRealYeti on 2008-06-20
Ok this is what I got:

ubuntu@ubuntu:~$ ls -l /media/disk/lib/init/
ls: cannot access /media/disk/lib/init/: No such file or directory

ubuntu@ubuntu:~$ ls -ld /media/disk/lib/init/
ls: cannot access /media/disk/lib/init/: No such file or directory

ubuntu@ubuntu:~$ ls -ld /media/disk/lib
drwxr-xr-x 14 root root 4096 2008-06-19 20:39 /media/disk/lib

there is no /init directory ??

there was one however in the lib64 directory so I ran the commands in there and got this:

ubuntu@ubuntu:~$ ls -l /media/disk/lib64/init/
total 24
-rwxr-xr-x 1 root root  2702 2008-04-18 16:02 mountall-net-fs
-rw-r--r-- 1 root root  3094 2008-04-18 16:02 mount-functions.sh
-rwxr-xr-x 1 root root 11224 2008-04-18 16:02 readlink
-rw-r--r-- 1 root root  5630 2008-04-18 16:02 usplash-fsck-functions.sh
-rw-r--r-- 1 root root   129 2008-04-18 16:02 vars.sh

ubuntu@ubuntu:~$ ls -ld /media/disk/lib64/init/
drwxr-xr-x 2 root root 110 2008-04-22 18:02 /media/disk/lib64/init/

FYI - I'm running the 64bit version 

As for what I did to get here i'm not sure.  The only thing i can think of is that i ran this commend

$mkdir /mnt/newhome

But from what I understand that just creates a new directory

---

### Post by TheRealYeti on 2008-06-20
Any one got any more ideas?

---

### Post by TheRealYeti on 2008-06-20
I'm thinking about just doing a reinstall. Is it possible to do a "repair" install.

Also i'm running a dual boot system with XP on another partition.  Is GRUB smart enough to know that the system's been reinstalled and allow me to boot correctly?

---

### Post by geirha on 2008-06-20
Since the live session on the cd has a /lib/init/ (I'm assuming it's a 64-bit CD), your system should probably have one too. /lib/init/vars.sh is installed by the package called initscripts. Try reinstalling it by doing the following from the live session:
```

# assuming / is mounted as /media/disk
sudo chroot /media/disk
aptitude reinstall initscripts
exit

```

---

### Post by VMC on 2008-06-20
> **TheRealYeti said:**
> I'm thinking about just doing a reinstall. Is it possible to do a "repair" install.

Also i'm running a dual boot system with XP on another partition.  Is GRUB smart enough to know that the system's been reinstalled and allow me to boot correctly?
If you re-install into the same partitions, it should build a new grub menu.lst detecting your Windows. Not to worry, that's a simple fix if it does wrong.

---

### Post by TheRealYeti on 2008-06-20
> **geirha said:**
> Since the live session on the cd has a /lib/init/ (I'm assuming it's a 64-bit CD), your system should probably have one too. /lib/init/vars.sh is installed by the package called initscripts. Try reinstalling it by doing the following from the live session:
```

# assuming / is mounted as /media/disk
sudo chroot /media/disk
aptitude reinstall initscripts
exit

```

there is not init directory in the following location /media/disk/lib

It seems to be missing I guess that's the problem.

I'll try you suggestion above and post the results

Thanks

---

### Post by TheRealYeti on 2008-06-20
Here's the results from your suggestion:

ubuntu@ubuntu:~$ sudo chroot /media/disk
root@ubuntu:/# aptitude reinstall initscripts
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done             
initscripts is not currently installed, so it will not be reinstalled.
initscripts is not currently installed, so it will not be reinstalled.
The following packages are unused and will be REMOVED:
  debhelper dpatch dpkg-dev gettext html2text intltool-debian kbuild 
  libtimedate-perl libvirt0 libxalan110 libxen3 libxerces27 
  module-assistant patch po-debconf vgabios 
0 packages upgraded, 0 newly installed, 16 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 26.1MB will be freed.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
Can not write log, openpty() failed (/dev/pts not mounted?)
(Reading database ... 155330 files and directories currently installed.)
Removing debhelper ...
Removing dpatch ...
Removing dpkg-dev ...
Removing po-debconf ...
/var/lib/dpkg/info/po-debconf.prerm: 7: cannot create /dev/null: Permission denied
Removing intltool-debian ...
Removing gettext ...
Removing html2text ...
/var/lib/dpkg/info/html2text.postrm: 4: cannot create /dev/null: Permission denied
Removing kbuild ...
Removing libtimedate-perl ...
Removing libvirt0 ...
/sbin/ldconfig: 15: cannot create /dev/null: Permission denied
Removing libxalan110 ...
/sbin/ldconfig: 15: cannot create /dev/null: Permission denied
Removing libxen3 ...
/sbin/ldconfig: 15: cannot create /dev/null: Permission denied
Removing libxerces27 ...
/sbin/ldconfig: 15: cannot create /dev/null: Permission denied
Removing module-assistant ...
Removing patch ...
Removing vgabios ...
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done  

just going to re boot to see if its worked.

---

### Post by geirha on 2008-06-20
The output says initscripts wasn't installed, so instead of "sudo aptitude reinstall initscripts", you'll need to do "sudo aptitude install initscripts".

---

### Post by TheRealYeti on 2008-06-20
Ok tried the install command but unsure weather it was sucessful:

root@ubuntu:/# aptitude install initscripts
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
The following NEW packages will be automatically installed:
  e2fsprogs libblkid1 
The following NEW packages will be installed:
  e2fsprogs initscripts libblkid1 
0 packages upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Need to get 471kB of archives. After unpacking 2380kB will be used.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
Get:1 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/main libblkid1 1.40.8-2ubuntu2 [52.5kB]
Get:2 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/main e2fsprogs 1.40.8-2ubuntu2 [353kB]
Get:3 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/main initscripts 2.86.ds1-14.1ubuntu45 [65.3kB]
Fetched 471kB in 2s (221kB/s)     
sh: cannot create /dev/null: Permission denied
sh: cannot create /dev/null: Permission denied
dpkg-preconfigure: unable to re-open stdin: 
Can not write log, openpty() failed (/dev/pts not mounted?)
Selecting previously deselected package libblkid1.
(Reading database ... 154334 files and directories currently installed.)
Unpacking libblkid1 (from .../libblkid1_1.40.8-2ubuntu2_amd64.deb) ...
Can not write log, openpty() failed (/dev/pts not mounted?)
Setting up libblkid1 (1.40.8-2ubuntu2) ...
/sbin/ldconfig: 15: cannot create /dev/null: Permission denied
/sbin/ldconfig: 15: cannot create /dev/null: Permission denied

Can not write log, openpty() failed (/dev/pts not mounted?)
Selecting previously deselected package e2fsprogs.
(Reading database ... 154339 files and directories currently installed.)
Unpacking e2fsprogs (from .../e2fsprogs_1.40.8-2ubuntu2_amd64.deb) ...
/var/lib/dpkg/tmp.ci/preinst: 3: cannot create /dev/null: Permission denied
This package requires features of dpkg unavailable in this version.
Please upgrade to a more recent version (>=1.1.0) of dpkg.
dpkg: error processing /var/cache/apt/archives/e2fsprogs_1.40.8-2ubuntu2_amd64.deb (--unpack):
 subprocess pre-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/e2fsprogs_1.40.8-2ubuntu2_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done             
root@ubuntu:/#

---

### Post by jimv on 2008-06-20
do

```
sudo aptitude install initscripts
```

---

### Post by TheRealYeti on 2008-06-20
Thank to all that helped.  i gave up in the end and did a reinstall which is working great.

---

### Post by jimv on 2008-06-20
Don't feel too bad.  I borked my server install last week by trying to uninstall some packages that I thought I didn't need.  Turns out that I did.  :(

---

