---
title: "Dandy little apt-get problem"
date: 2007-11-14
forum: General Help
---

### Post by xlr8ed on 2007-11-14
So anything that I attempt to install or update ends like the following. I'm running 7.10 and so far it's been very stable and I haven't added anything since the first night I configured the machine. There is no wireless devices on this box and it serves as a Samba/Apache/Mysql server. I checked and rt2500usb.ko is located in the directory referenced.

Help! and thanks in advance.


jason@grover:~$ sudo apt-get install thunderbird
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  thunderbird-gnome-support latex-xft-fonts
The following NEW packages will be installed:
  thunderbird
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 11.0MB of archives.
After unpacking 32.8MB of additional disk space will be used.
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main thunderbird 2.0.0.8~pre071022+nobinonly-0ubuntu0.7.10 [11.0MB]
Fetched 11.0MB in 24s (440kB/s)                                                                                                    
Selecting previously deselected package thunderbird.
(Reading database ... 108725 files and directories currently installed.)
Unpacking thunderbird (from .../thunderbird_2.0.0.8~pre071022+nobinonly-0ubuntu0.7.10_i386.deb) ...
[B]Setting up linux-restricted-modules-2.6.22-14-generic (2.6.22.4-14.10) ...
WARNING: Can't read module /lib/modules/2.6.22-14-generic/ubuntu/wireless/rt2x00/rt2500usb.ko: No such device or address[/B]
dpkg: error processing linux-restricted-modules-2.6.22-14-generic (--configure):
 subprocess post-installation script killed by signal (Interrupt)
Setting up thunderbird (2.0.0.8~pre071022+nobinonly-0ubuntu0.7.10) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 linux-restricted-modules-2.6.22-14-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by x64Jimbo on 2007-11-14
have you tried removing that problem package, since it seems you don't need it?

---

### Post by Vince4Amy on 2007-11-14
Does sudo apt-get install -f do anything?

---

### Post by xlr8ed on 2007-11-14
> **x64Jimbo said:**
> have you tried removing that problem package, since it seems you don't need it?

if you mean linux-restricted-modules-2.6.22-14-generic, then I have and I end up with the same thing


> **Vince4Amy said:**
> Does sudo apt-get install -f do anything?

Again, same issue.


I also took a look at the permissions and this is what's what...even trying to sudo chmod, chown or even rm results in futility.

jason@grover:/home$ ls -alh /lib/modules/2.6.22-14-generic/ubuntu/wireless/rt2x00/
total 72K
drwxr-xr-x  2 root      root        4.0K 2007-10-15 18:20 .
drwxr-xr-x 13 root      root        4.0K 2007-11-03 12:46 ..
c--s--s--T  1 860431368 2643992874 70, 1 1973-10-04 00:16 rt2500usb.ko
-rw-r--r--  1 root      root         30K 2007-10-13 00:43 rt61pci.ko
-rw-r--r--  1 root      root         32K 2007-10-13 00:43 rt73usb.ko
jason@grover:/home$

---

### Post by xlr8ed on 2007-11-14
> **xlr8ed said:**
> [B]Setting up linux-restricted-modules-2.6.22-14-generic (2.6.22.4-14.10) ...
WARNING: Can't read module /lib/modules/2.6.22-14-generic/ubuntu/wireless/rt2x00/rt2500usb.ko: No such device or address[/B]

Ok, I got pass this by booting off the LiveCD, mounting my root partition and copying rt2500usb.ko over.

However when ever I try to apt-get anything I get

Setting up linux-restricted-modules-2.6.22-14-generic (2.6.22.4-14.10)

Any ideas??

---

