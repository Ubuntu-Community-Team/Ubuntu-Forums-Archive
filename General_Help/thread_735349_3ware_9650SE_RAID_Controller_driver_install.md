---
title: "3ware 9650SE RAID Controller driver install"
date: 2008-03-25
forum: General Help
---

### Post by yavor on 2008-03-25
Hello everyone,

I'm trying to install a 3ware 9650SE raid controller driver on a ubuntu system:
> root@server:~ # uname -a
Linux server 2.6.10-5-386 #1 Tue Apr 5 12:12:40 UTC 2005 i686 GNU/Linux


When i run make i get the following error:
> root@server:~ # cd driver/
root@server:~/driver # ll
total 112
-rw-r--r-- 1 root root 76607 2007-06-14 22:36 3w-9xxx.c
-rw-r--r-- 1 root root 26328 2007-06-14 22:36 3w-9xxx.h
-rw-r--r-- 1 root root   398 2007-06-14 22:36 Makefile
root@server:~/driver # make
make V=1 -I/lib/modules/2.6.10-5-386/source/drivers/scsi -C /lib/modules/2.6.10-5-386/source SUBDIRS=/root/driver modules
make: *** /lib/modules/2.6.10-5-386/source: No such file or directory.  Stop.
make: *** [default] Error 2


Could someone help me?

Thanks

---

### Post by yavor on 2008-03-25
I've added 3w-9xxx to my /etc/modules and after reboot:
> root@server:~ # dmesg
3ware 9000 Storage Controller device driver for Linux v2.26.02.001.
root@server:~ # lsmod
3w_9xxx                31620  0
scsi_mod              119936  5 3w_9xxx,sd_mod,sr_mod,sg,libata
root@server:~ # lspci
0000:01:00.0 RAID bus controller: 3ware Inc: Unknown device 1004 (rev 01)

But there is no new device in /dev for my raid 1 array.

---

### Post by dean123 on 2008-03-28
> **yavor said:**
> Hello everyone,

I'm trying to install a 3ware 9650SE raid controller driver on a ubuntu system:


When i run make i get the following error:


Could someone help me?

Thanks

You need to install linux headers and gcc stuff.

# sudo -s  (root access)
# cd /usr/src
# apt-get install build-essential
# apt-get install linux-headers-`uname -r`

uname -r is your kernel 2.6.10...

# ln -s /usr/src/linux-headers-<kernel>  linux

Now runnming "make" will work.  Good luck.

---

