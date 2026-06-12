---
title: "Restore /var/lib/dpkg/*"
date: 2007-10-11
forum: General Help
---

### Post by emil.s on 2007-10-11
in an accident, i removed the whole /var/lib/dpkg directory...
I have restored the status file from /var/backups, but there is still missing files think.

"apt-get update" works, but i can't install anything or upgrade the system:
```
root@servern: /home/emil # apt-get dist-upgrade 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be upgraded:
  apt apt-utils linux-image-2.6.22-14-server linux-image-server linux-libc-dev linux-server linux-ubuntu-modules-2.6.22-14-server
  ubuntu-standard x11-common
9 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
3 not fully installed or removed.
Need to get 0B/24.5MB of archives.
After unpacking 73.7MB of additional disk space will be used.
Do you want to continue [Y/n]? 
Preconfiguring packages ...
FATAL: Module battery not found.
(Reading database ... 
dpkg: serious warning: files list file for package `tcpd' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `libtext-wrapi18n-perl' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `fortunes' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `debconf' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `librecode0' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `hddtemp' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `memtest86+' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `dash' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `libart-2.0-2' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `mktemp' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `libt1-5' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `libpq5' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `libxdmcp6' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `rtorrent' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `coreutils' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `sudo' missing, assuming package has no files currently installed.

..............
..............
..............
..............


dpkg: serious warning: files list file for package `libxau6' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `dhcp3-server' missing, assuming package has no files currently installed.
0 files and directories currently installed.)
Preparing to replace linux-image-2.6.22-14-server 2.6.22-14.41 (using .../linux-image-2.6.22-14-server_2.6.22-14.43_i386.deb) ...
Done.
Unpacking replacement linux-image-2.6.22-14-server ...
dpkg: error processing /var/cache/apt/archives/linux-image-2.6.22-14-server_2.6.22-14.43_i386.deb (--unpack):
 unable to create updated files list file for package linux-image-2.6.22-14-server: No such file or directory
Preparing to replace linux-ubuntu-modules-2.6.22-14-server 2.6.22-14.35 (using .../linux-ubuntu-modules-2.6.22-14-server_2.6.22-14.35_i386.deb) ...
Unpacking replacement linux-ubuntu-modules-2.6.22-14-server ...
dpkg: error processing /var/cache/apt/archives/linux-ubuntu-modules-2.6.22-14-server_2.6.22-14.35_i386.deb (--unpack):
 unable to create updated files list file for package linux-ubuntu-modules-2.6.22-14-server: No such file or directory
Preparing to replace apt 0.7.6ubuntu12 (using .../apt_0.7.6ubuntu13_i386.deb) ...
Unpacking replacement apt ...
dpkg: error processing /var/cache/apt/archives/apt_0.7.6ubuntu13_i386.deb (--unpack):
 unable to create updated files list file for package apt: No such file or directory
Errors were encountered while processing:
 /var/cache/apt/archives/linux-image-2.6.22-14-server_2.6.22-14.43_i386.deb
 /var/cache/apt/archives/linux-ubuntu-modules-2.6.22-14-server_2.6.22-14.35_i386.deb
 /var/cache/apt/archives/apt_0.7.6ubuntu13_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

How do i solve this?

---

### Post by az on 2007-10-11
Try 

sudo dpkg --clear-avail

and then

sudo apt-get update

---

### Post by emil.s on 2007-10-11
No difference... :(
"unable to create updated files list file for package apt: No such file or directory"

Is it possible to force reinstall every package which is installed on the system (read from status file), so the file list files will be restored?
```
dpkg: serious warning: files list file for package `*everything*' missing, assuming package has no files currently installed.
```

---

### Post by eph1973 on 2007-10-11
Not sure if this will work, but you could try:
```
sudo dpkg --recursive -A /var/cache/apt/archives
```

---

### Post by emil.s on 2007-10-12
> **eph1973 said:**
> Not sure if this will work, but you could try:
```
sudo dpkg --recursive -A /var/cache/apt/archives
```

Didn't work... :(

---

### Post by eph1973 on 2007-10-12
OK, try this.  Ensure you have a wired internet connection.  Boot from the live CD.  Go to the terminal in the Live CD, then figure out which directory your hard drive root is on.  It will be something like /media/disk.  You may have /media/disk /media/disk1 and so on, depending on how many partitions you have, and how many HD's you have.  Once you figure out which one your root directory is, try the following (for this, let's assume /media/disk)
```

sudo chroot /media/disk apt-get install dpkg
```

This should reinstall dpkg onto your hard drive from the repositories using the LiveCD's version of apt-get.

---

### Post by emil.s on 2007-10-16
> **eph1973 said:**
> OK, try this.  Ensure you have a wired internet connection.  Boot from the live CD.  Go to the terminal in the Live CD, then figure out which directory your hard drive root is on.  It will be something like /media/disk.  You may have /media/disk /media/disk1 and so on, depending on how many partitions you have, and how many HD's you have.  Once you figure out which one your root directory is, try the following (for this, let's assume /media/disk)
```

sudo chroot /media/disk apt-get install dpkg
```

This should reinstall dpkg onto your hard drive from the repositories using the LiveCD's version of apt-get.

Still the same error! :( Is there any more ways to try, or is a new install next...? :confused:

---

### Post by eph1973 on 2007-10-17
There is only one more thing I can think of to do.  You might have to see if you can download a dpkg.tar.gz file, which you can locate [here]("http://packages.debian.org/etch/dpkg"), then install it that way into your root directory with the makefile that should come with it.   It may be easier and less accident prone to do a reinstall, especially if your /home directory is on a separate partition.  It should only take between 30 minutes and an hour to do a reinstall (after backing up your data), depending on your proficiency at it.  Unless, of course, someone else is privy to the solution to your problem.

---

### Post by emil.s on 2007-10-17
> **eph1973 said:**
> There is only one more thing I can think of to do.  You might have to see if you can download a dpkg.tar.gz file, which you can locate [here]("http://packages.debian.org/etch/dpkg"), then install it that way into your root directory with the makefile that should come with it.   It may be easier and less accident prone to do a reinstall, especially if your /home directory is on a separate partition.  It should only take between 30 minutes and an hour to do a reinstall (after backing up your data), depending on your proficiency at it.  Unless, of course, someone else is privy to the solution to your problem.

Ok... I think reinstalling is easier. I don't have GCC installed... :P

Thanks anyway!

---

