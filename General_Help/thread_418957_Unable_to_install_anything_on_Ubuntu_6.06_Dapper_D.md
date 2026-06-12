---
title: "Unable to install anything on Ubuntu 6.06 Dapper Drake"
date: 2007-04-22
forum: General Help
---

### Post by Shaymus22 on 2007-04-22
I'm really, REALLY sorry for all of the code I'm going to have to post. Also, something that you should know is that I'm pretty new to Ubuntu, Linux, and UNIX. I'd like to think that I've learned a lot, and I have, but in truth I know just enough to not be naive enough to think that I know anything. The reason I'm telling you this is that if you're going to post help, make sure not to leave any gaps that you might expect someone with experience to be able to fill in.

With that out of the way, here's my problem:
Every time I try to install anything with Add/Remove Applications, it gives me this error (for this example, I was trying to install iPodder...the installation failed the first time):

The following problems were found on your system:
```

E: /var/cache/apt/archives/libx11-6_2%3a1.0.0-0ubuntu9_i386.deb: unable to create updated files list file for package libx11-6
E: /var/cache/apt/archives/libx11-dev_2%3a1.0.0-0ubuntu9_i386.deb: unable to create updated files list file for package libx11-dev
E: /var/cache/apt/archives/locales_2.3.18.3_all.deb: unable to create updated files list file for package locales
E: /var/cache/apt/archives/makedev_2.3.1-79ubuntu1_all.deb: unable to create updated files list file for package makedev
E: /var/cache/apt/archives/app-install-data-commercial_5.5_all.deb: unable to create updated files list file for package app-install-data-commercial
E: /var/cache/apt/archives/libhal1_0.5.7-1ubuntu18.2_i386.deb: unable to create updated files list file for package libhal1
E: /var/cache/apt/archives/hal_0.5.7-1ubuntu18.2_i386.deb: unable to create updated files list file for package hal
E: /var/cache/apt/archives/hal-device-manager_0.5.7-1ubuntu18.2_all.deb: unable to create updated files list file for package hal-device-manager
E: /var/cache/apt/archives/xmms_1.2.10+cvs20050809-4ubuntu5.1_i386.deb: unable to create updated files list file for package xmms
E: /var/cache/apt/archives/python2.4-xmms_2.06-3ubuntu1_i386.deb: unable to create updated files list file for package python2.4-xmms
E: /var/cache/apt/archives/python-xmms_2.06-3ubuntu1_all.deb: unable to create updated files list file for package python-xmms
E: /var/cache/apt/archives/python-wxversion_2.6.1.2ubuntu2_all.deb: unable to create updated files list file for package python-wxversion
E: /var/cache/apt/archives/python-wxgtk2.6_2.6.1.2ubuntu2_i386.deb: unable to create updated files list file for package python-wxgtk2.6
E: /var/cache/apt/archives/python2.4-pyrss2gen_1.0.0-1_all.deb: unable to create updated files list file for package python2.4-pyrss2gen
E: /var/cache/apt/archives/python-pyrss2gen_1.0.0-1_all.deb: unable to create updated files list file for package python-pyrss2gen
E: /var/cache/apt/archives/python-feedparser_4.1-2ubuntu1_all.deb: unable to create updated files list file for package python-feedparser
E: /var/cache/apt/archives/ipodder_2.1.9-4_all.deb: unable to create updated files list file for package ipodder
E: /var/cache/apt/archives/libqt3-mt_3%3a3.3.6-1ubuntu6.2_i386.deb: unable to create updated files list file for package libqt3-mt
E: /var/cache/apt/archives/kdelibs-data_4%3a3.5.2-0ubuntu18.4_all.deb: unable to create updated files list file for package kdelibs-data
E: /var/cache/apt/archives/kdelibs4c2a_4%3a3.5.2-0ubuntu18.4_i386.deb: unable to create updated files list file for package kdelibs4c2a
E: /var/cache/apt/archives/kdelibs-bin_4%3a3.5.2-0ubuntu18.4_i386.deb: unable to create updated files list file for package kdelibs-bin
E: /var/cache/apt/archives/libhal-storage1_0.5.7-1ubuntu18.2_i386.deb: unable to create updated files list file for package libhal-storage1
E: /var/cache/apt/archives/libxine-extracodecs_1.1.1+ubuntu1-2_i386.deb: unable to create updated files list file for package libxine-extracodecs
E: /var/cache/apt/archives/linux-headers-2.6.15-28_2.6.15-28.53_i386.deb: unable to create updated files list file for package linux-headers-2.6.15-28
E: /var/cache/apt/archives/linux-headers-2.6.15-28-386_2.6.15-28.53_i386.deb: unable to create updated files list file for package linux-headers-2.6.15-28-386
E: /var/cache/apt/archives/linux-image-2.6.15-28-386_2.6.15-28.53_i386.deb: unable to create updated files list file for package linux-image-2.6.15-28-386
E: /var/cache/apt/archives/pmount_0.9.11-1ubuntu1_i386.deb: unable to create updated files list file for package pmount
E: /var/cache/apt/archives/wine_0.9.35~winehq0~ubuntu~6.06-1_i386.deb: unable to create updated files list file for package wine

```

If I try apt-get install ipodder, I get this (if I'm not root I use sudo apt-get install ipodder):

[there's more, but it wasn't saved by the Terminal; it's pretty much the same as what you see directly above]
```

dpkg: serious warning: files list file for package `usplash' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `libid3tag0' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `libcupsimage2' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `libgnutls12' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `libwrap0' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `xserver-xorg-driver-via' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `netcat' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `oclock' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `lsof' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `python2.4-soappy' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `python-pyogg' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `ttf-bengali-fonts' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `libxau6' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `liblaunchpad-integration0' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `libbtctl2' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `gnome-power-manager' missing, assuming package has no files currently installed.
65 files and directories currently installed.)
Preparing to replace libx11-6 2:1.0.0-0ubuntu9 (using .../libx11-6_2%3a1.0.0-0ubuntu9_i386.deb) ...
Unpacking replacement libx11-6 ...
dpkg: error processing /var/cache/apt/archives/libx11-6_2%3a1.0.0-0ubuntu9_i386.deb (--unpack):
 unable to create updated files list file for package libx11-6: No such file or directory
Preparing to replace libx11-dev 2:1.0.0-0ubuntu9 (using .../libx11-dev_2%3a1.0.0-0ubuntu9_i386.deb) ...
Unpacking replacement libx11-dev ...
dpkg: error processing /var/cache/apt/archives/libx11-dev_2%3a1.0.0-0ubuntu9_i386.deb (--unpack):
 unable to create updated files list file for package libx11-dev: No such file or directory
Preparing to replace locales 2.3.18.2 (using .../locales_2.3.18.3_all.deb) ...
Unpacking replacement locales ...
dpkg: error processing /var/cache/apt/archives/locales_2.3.18.3_all.deb (--unpack):
 unable to create updated files list file for package locales: No such file or directory
Preparing to replace makedev 2.3.1-79ubuntu1 (using .../makedev_2.3.1-79ubuntu1_all.deb) ...
Unpacking replacement makedev ...
dpkg: error processing /var/cache/apt/archives/makedev_2.3.1-79ubuntu1_all.deb (--unpack):
 unable to create updated files list file for package makedev: No such file or directory
Preparing to replace app-install-data-commercial 5.3 (using .../app-install-data-commercial_5.5_all.deb) ...
Unpacking replacement app-install-data-commercial ...
dpkg: error processing /var/cache/apt/archives/app-install-data-commercial_5.5_all.deb (--unpack):
 unable to create updated files list file for package app-install-data-commercial: No such file or directory
Preparing to replace libhal1 0.5.7-1ubuntu18.2 (using .../libhal1_0.5.7-1ubuntu18.2_i386.deb) ...
Unpacking replacement libhal1 ...
dpkg: error processing /var/cache/apt/archives/libhal1_0.5.7-1ubuntu18.2_i386.deb (--unpack):
 unable to create updated files list file for package libhal1: No such file or directory
Preparing to replace hal 0.5.7-1ubuntu18.2 (using .../hal_0.5.7-1ubuntu18.2_i386.deb) ...
Unpacking replacement hal ...
dpkg: error processing /var/cache/apt/archives/hal_0.5.7-1ubuntu18.2_i386.deb (--unpack):
 unable to create updated files list file for package hal: No such file or directory
Preparing to replace hal-device-manager 0.5.7-1ubuntu18.2 (using .../hal-device-manager_0.5.7-1ubuntu18.2_all.deb) ...
Unpacking replacement hal-device-manager ...
dpkg: error processing /var/cache/apt/archives/hal-device-manager_0.5.7-1ubuntu18.2_all.deb (--unpack):
 unable to create updated files list file for package hal-device-manager: No such file or directory
Preparing to replace xmms 1.2.10+cvs20050809-4ubuntu5.1 (using .../xmms_1.2.10+cvs20050809-4ubuntu5.1_i386.deb) ...
Unpacking replacement xmms ...
dpkg: error processing /var/cache/apt/archives/xmms_1.2.10+cvs20050809-4ubuntu5.1_i386.deb (--unpack):
 unable to create updated files list file for package xmms: No such file or directory
Preparing to replace python2.4-xmms 2.06-3ubuntu1 (using .../python2.4-xmms_2.06-3ubuntu1_i386.deb) ...
Unpacking replacement python2.4-xmms ...
dpkg: error processing /var/cache/apt/archives/python2.4-xmms_2.06-3ubuntu1_i386.deb (--unpack):
 unable to create updated files list file for package python2.4-xmms: No such file or directory
Preparing to replace python-xmms 2.06-3ubuntu1 (using .../python-xmms_2.06-3ubuntu1_all.deb) ...
Unpacking replacement python-xmms ...
dpkg: error processing /var/cache/apt/archives/python-xmms_2.06-3ubuntu1_all.deb (--unpack):
 unable to create updated files list file for package python-xmms: No such file or directory
Preparing to replace python-wxversion 2.6.1.2ubuntu2 (using .../python-wxversion_2.6.1.2ubuntu2_all.deb) ...
Unpacking replacement python-wxversion ...
dpkg: error processing /var/cache/apt/archives/python-wxversion_2.6.1.2ubuntu2_all.deb (--unpack):
 unable to create updated files list file for package python-wxversion: No such file or directory
Preparing to replace python-wxgtk2.6 2.6.1.2ubuntu2 (using .../python-wxgtk2.6_2.6.1.2ubuntu2_i386.deb) ...
Unpacking replacement python-wxgtk2.6 ...
dpkg: error processing /var/cache/apt/archives/python-wxgtk2.6_2.6.1.2ubuntu2_i386.deb (--unpack):
 unable to create updated files list file for package python-wxgtk2.6: No such file or directory
Preparing to replace python2.4-pyrss2gen 1.0.0-1 (using .../python2.4-pyrss2gen_1.0.0-1_all.deb) ...
Unpacking replacement python2.4-pyrss2gen ...
dpkg: error processing /var/cache/apt/archives/python2.4-pyrss2gen_1.0.0-1_all.deb (--unpack):
 unable to create updated files list file for package python2.4-pyrss2gen: No such file or directory
Preparing to replace python-pyrss2gen 1.0.0-1 (using .../python-pyrss2gen_1.0.0-1_all.deb) ...
Unpacking replacement python-pyrss2gen ...
dpkg: error processing /var/cache/apt/archives/python-pyrss2gen_1.0.0-1_all.deb (--unpack):
 unable to create updated files list file for package python-pyrss2gen: No such file or directory
Preparing to replace python-feedparser 4.1-2ubuntu1 (using .../python-feedparser_4.1-2ubuntu1_all.deb) ...
Unpacking replacement python-feedparser ...
dpkg: error processing /var/cache/apt/archives/python-feedparser_4.1-2ubuntu1_all.deb (--unpack):
 unable to create updated files list file for package python-feedparser: No such file or directory
Preparing to replace ipodder 2.1.9-4 (using .../ipodder_2.1.9-4_all.deb) ...
Unpacking replacement ipodder ...
dpkg: error processing /var/cache/apt/archives/ipodder_2.1.9-4_all.deb (--unpack):
 unable to create updated files list file for package ipodder: No such file or directory
Preparing to replace libqt3-mt 3:3.3.6-1ubuntu6.1 (using .../libqt3-mt_3%3a3.3.6-1ubuntu6.2_i386.deb) ...
Unpacking replacement libqt3-mt ...
dpkg: error processing /var/cache/apt/archives/libqt3-mt_3%3a3.3.6-1ubuntu6.2_i386.deb (--unpack):
 unable to create updated files list file for package libqt3-mt: No such file or directory
Preparing to replace kdelibs-data 4:3.5.2-0ubuntu18.3 (using .../kdelibs-data_4%3a3.5.2-0ubuntu18.4_all.deb) ...
Unpacking replacement kdelibs-data ...
dpkg: error processing /var/cache/apt/archives/kdelibs-data_4%3a3.5.2-0ubuntu18.4_all.deb (--unpack):
 unable to create updated files list file for package kdelibs-data: No such file or directory
Preparing to replace kdelibs4c2a 4:3.5.2-0ubuntu18.3 (using .../kdelibs4c2a_4%3a3.5.2-0ubuntu18.4_i386.deb) ...
Unpacking replacement kdelibs4c2a ...
dpkg: error processing /var/cache/apt/archives/kdelibs4c2a_4%3a3.5.2-0ubuntu18.4_i386.deb (--unpack):
 unable to create updated files list file for package kdelibs4c2a: No such file or directory
Preparing to replace kdelibs-bin 4:3.5.2-0ubuntu18.3 (using .../kdelibs-bin_4%3a3.5.2-0ubuntu18.4_i386.deb) ...
Unpacking replacement kdelibs-bin ...
dpkg: error processing /var/cache/apt/archives/kdelibs-bin_4%3a3.5.2-0ubuntu18.4_i386.deb (--unpack):
 unable to create updated files list file for package kdelibs-bin: No such file or directory
Preparing to replace libhal-storage1 0.5.7-1ubuntu18.2 (using .../libhal-storage1_0.5.7-1ubuntu18.2_i386.deb) ...
Unpacking replacement libhal-storage1 ...
dpkg: error processing /var/cache/apt/archives/libhal-storage1_0.5.7-1ubuntu18.2_i386.deb (--unpack):
 unable to create updated files list file for package libhal-storage1: No such file or directory
Preparing to replace libxine-extracodecs 1.1.1+ubuntu1-2 (using .../libxine-extracodecs_1.1.1+ubuntu1-2_i386.deb) ...
Unpacking replacement libxine-extracodecs ...
dpkg: error processing /var/cache/apt/archives/libxine-extracodecs_1.1.1+ubuntu1-2_i386.deb (--unpack):
 unable to create updated files list file for package libxine-extracodecs: No such file or directory
Preparing to replace linux-headers-2.6.15-28 2.6.15-28.51 (using .../linux-headers-2.6.15-28_2.6.15-28.53_i386.deb) ...
Unpacking replacement linux-headers-2.6.15-28 ...
dpkg: error processing /var/cache/apt/archives/linux-headers-2.6.15-28_2.6.15-28.53_i386.deb (--unpack):
 unable to create updated files list file for package linux-headers-2.6.15-28: No such file or directory
Preparing to replace linux-headers-2.6.15-28-386 2.6.15-28.51 (using .../linux-headers-2.6.15-28-386_2.6.15-28.53_i386.deb) ...
Unpacking replacement linux-headers-2.6.15-28-386 ...
dpkg: error processing /var/cache/apt/archives/linux-headers-2.6.15-28-386_2.6.15-28.53_i386.deb (--unpack):
 unable to create updated files list file for package linux-headers-2.6.15-28-386: No such file or directory
Preparing to replace linux-image-2.6.15-28-386 2.6.15-28.51 (using .../linux-image-2.6.15-28-386_2.6.15-28.53_i386.deb) ...
The directory /lib/modules/2.6.15-28-386 still exists. Continuing as directed.
Unpacking replacement linux-image-2.6.15-28-386 ...
dpkg: error processing /var/cache/apt/archives/linux-image-2.6.15-28-386_2.6.15-28.53_i386.deb (--unpack):
 unable to create updated files list file for package linux-image-2.6.15-28-386: No such file or directory
Preparing to replace pmount 0.9.11-1ubuntu1 (using .../pmount_0.9.11-1ubuntu1_i386.deb) ...
Unpacking replacement pmount ...
dpkg: error processing /var/cache/apt/archives/pmount_0.9.11-1ubuntu1_i386.deb (--unpack):
 unable to create updated files list file for package pmount: No such file or directory
Preparing to replace wine 0.9.34~winehq0~ubuntu~6.06-1 (using .../wine_0.9.35~winehq0~ubuntu~6.06-1_i386.deb) ...
Unpacking replacement wine ...
dpkg: error processing /var/cache/apt/archives/wine_0.9.35~winehq0~ubuntu~6.06-1_i386.deb (--unpack):
 unable to create updated files list file for package wine: No such file or directory
Errors were encountered while processing:
 /var/cache/apt/archives/libx11-6_2%3a1.0.0-0ubuntu9_i386.deb
 /var/cache/apt/archives/libx11-dev_2%3a1.0.0-0ubuntu9_i386.deb
 /var/cache/apt/archives/locales_2.3.18.3_all.deb
 /var/cache/apt/archives/makedev_2.3.1-79ubuntu1_all.deb
 /var/cache/apt/archives/app-install-data-commercial_5.5_all.deb
 /var/cache/apt/archives/libhal1_0.5.7-1ubuntu18.2_i386.deb
 /var/cache/apt/archives/hal_0.5.7-1ubuntu18.2_i386.deb
 /var/cache/apt/archives/hal-device-manager_0.5.7-1ubuntu18.2_all.deb
 /var/cache/apt/archives/xmms_1.2.10+cvs20050809-4ubuntu5.1_i386.deb
 /var/cache/apt/archives/python2.4-xmms_2.06-3ubuntu1_i386.deb
 /var/cache/apt/archives/python-xmms_2.06-3ubuntu1_all.deb
 /var/cache/apt/archives/python-wxversion_2.6.1.2ubuntu2_all.deb
 /var/cache/apt/archives/python-wxgtk2.6_2.6.1.2ubuntu2_i386.deb
 /var/cache/apt/archives/python2.4-pyrss2gen_1.0.0-1_all.deb
 /var/cache/apt/archives/python-pyrss2gen_1.0.0-1_all.deb
 /var/cache/apt/archives/python-feedparser_4.1-2ubuntu1_all.deb
 /var/cache/apt/archives/ipodder_2.1.9-4_all.deb
 /var/cache/apt/archives/libqt3-mt_3%3a3.3.6-1ubuntu6.2_i386.deb
 /var/cache/apt/archives/kdelibs-data_4%3a3.5.2-0ubuntu18.4_all.deb
 /var/cache/apt/archives/kdelibs4c2a_4%3a3.5.2-0ubuntu18.4_i386.deb
 /var/cache/apt/archives/kdelibs-bin_4%3a3.5.2-0ubuntu18.4_i386.deb
 /var/cache/apt/archives/libhal-storage1_0.5.7-1ubuntu18.2_i386.deb
 /var/cache/apt/archives/libxine-extracodecs_1.1.1+ubuntu1-2_i386.deb
 /var/cache/apt/archives/linux-headers-2.6.15-28_2.6.15-28.53_i386.deb
 /var/cache/apt/archives/linux-headers-2.6.15-28-386_2.6.15-28.53_i386.deb
 /var/cache/apt/archives/linux-image-2.6.15-28-386_2.6.15-28.53_i386.deb
 /var/cache/apt/archives/pmount_0.9.11-1ubuntu1_i386.deb
 /var/cache/apt/archives/wine_0.9.35~winehq0~ubuntu~6.06-1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@lee-desktop:/home#
```

How do I fix this?

Thank you for your time
--Shaymus22

---

### Post by dcstar on 2007-04-22
> **Shaymus22 said:**
> I'm really, REALLY sorry for all of the code I'm going to have to post. Also, something that you should know is that I'm pretty new to Ubuntu, Linux, and UNIX. I'd like to think that I've learned a lot, and I have, but in truth I know just enough to not be naive enough to think that I know anything. The reason I'm telling you this is that if you're going to post help, make sure not to leave any gaps that you might expect someone with experience to be able to fill in.

With that out of the way, here's my problem:
Every time I try to install anything with Add/Remove Applications, it gives me this error (for this example, I was trying to install iPodder...the installation failed the first time):
...........
How do I fix this?

Thank you for your time
--Shaymus22

Firstly check that you have not run out of disk space on your root partition, and then you need to check that you have network connectivity to the repositories.

---

### Post by Shaymus22 on 2007-04-22
Still doesn't work...I have >9GB of free space on the Ubuntu partition, and am connected to all four repositories

---

### Post by zvacet on 2007-04-23
```
sudo aptitude update
```

---

### Post by Shaymus22 on 2007-04-23
> **zvacet said:**
> ```
sudo aptitude update
```

That returns this 
[http://pastebin.ubuntu-uk.org/88](http://pastebin.ubuntu-uk.org/88)

---

### Post by Shaymus22 on 2007-04-23
sudo apt-get install **bump**

---

### Post by Shaymus22 on 2007-04-23
You know, I used to look down on people who bump their threads, but now that I'm in this position, I suddenly realize that it's not so bad

---

### Post by Shaymus22 on 2007-04-23
Surprisingly, my problem has not solved itself

---

### Post by j002 on 2007-04-23
1.  What are you installing from, internet, HDD or CD ?

2.  What happens in Synaptic Package Manager ?

---

### Post by Shaymus22 on 2007-04-24
> **j002 said:**
> 1.  What are you installing from, internet, HDD or CD ?

2.  What happens in Synaptic Package Manager ?

1) From the Internet
2) The same thing

---

### Post by strabes on 2007-04-24
You might have conflicting sources. Try replacing your sources.list with the dapper one here: [http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

---

### Post by Shaymus22 on 2007-04-27
Nope...still doesn't work :(

---

### Post by Shaymus22 on 2007-04-29
Checked again...it still doesn't work

---

### Post by Shaymus22 on 2007-05-02
It still doesn't work!

---

