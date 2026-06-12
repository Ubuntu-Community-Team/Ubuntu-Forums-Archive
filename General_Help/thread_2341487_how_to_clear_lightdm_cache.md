---
title: "how to clear lightdm cache ?"
date: 2016-10-28
forum: General Help
---

### Post by linuxcss2 on 2016-10-28
planning to run updates ... see have little space left in root partition
I find /var/lib/lightdm/.cache has a whopping 12GB tied up,
How can I clear that cache safely ?

running xubuntu 14.04 LTS

thanks
linuxcss

---

### Post by HereInOz on 2016-10-29
Bleachbit may be able to assist.  install it from the repos and then have a look through what it offers.  You may find an option there.  

Sorry for not being 100% sure, but I don't have a machine running Xubuntu, so can't test.

---

### Post by vasa1 on 2016-10-29
> **linuxcss2 said:**
> planning to run updates ... see have little space left in root partition
I find /var/lib/lightdm/.cache has a whopping 12GB tied up,
How can I clear that cache safely ?

running xubuntu 14.04 LTS

thanks
linuxcss

Please post the output of ```
ls -l /boot
```
and ```
df -h
```
Is your system encrypted?

Also provide the output of ```
sudo apt-get autoremove
``` Press **N**, if the output is overwhelming!

---

### Post by linuxcss2 on 2016-10-29
found the file that is huge!
```
root@csspc-base:/var/lib/lightdm/.cache"]root@csspc-base:/var/lib/lightdm/.cache/upstart# ls -hl
total 12G
-rw-r----- 1 lightdm lightdm 2.4M Oct 29 18:28 indicator-application.log
-rw-r----- 1 lightdm lightdm 525K Oct 29 18:28 indicator-messages.log
-rw-r----- 1 lightdm lightdm 6.5M Oct 29 18:28 indicator-power.log
-rw-r----- 1 lightdm lightdm  12G Oct 29 18:28 indicator-sound.log
root@csspc-base:/var/lib/lightdm/.cache"]root@csspc-base:/var/lib/lightdm/.cache/upstart# 

```
I zapped file with:
```
root@csspc-base:/var/lib/lightdm/.cache]root@csspc-base:/var/lib/lightdm/.cache/upstart# echo  > indicator-sound.log
``` 

saw bunch of error messages some with volume ... I'll have to pay attention to why it got
so huge .

your queries requests follow:


```
paul@csspc-base:~$ ls -l /boot
total 175048
-rw-r--r-- 1 root root  1164806 Jun 17  2015 abi-3.13.0-55-generic
-rw-r--r-- 1 root root  1164984 Jun 19  2015 abi-3.13.0-57-generic
-rw-r--r-- 1 root root  1165261 Aug 11  2015 abi-3.13.0-62-generic
-rw-r--r-- 1 root root  1165260 Nov  6  2015 abi-3.13.0-68-generic
-rw-r--r-- 1 root root  1165952 Mar 17  2016 abi-3.13.0-85-generic
-rw-r--r-- 1 root root  1166060 Jun  8 19:32 abi-3.13.0-88-generic
-rw-r--r-- 1 root root   165762 Jun 17  2015 config-3.13.0-55-generic
-rw-r--r-- 1 root root   165762 Jun 19  2015 config-3.13.0-57-generic
-rw-r--r-- 1 root root   165763 Aug 11  2015 config-3.13.0-62-generic
-rw-r--r-- 1 root root   165763 Nov  6  2015 config-3.13.0-68-generic
-rw-r--r-- 1 root root   165918 Mar 17  2016 config-3.13.0-85-generic
-rw-r--r-- 1 root root   165929 Jun  8 19:32 config-3.13.0-88-generic
drwxr-xr-x 3 root root     4096 Jun 27 13:01 extlinux
drwxr-xr-x 5 root root     4096 Jun 27 13:01 grub
-rw-r--r-- 1 root root 19213412 Jun 22  2015 initrd.img-3.13.0-55-generic
-rw-r--r-- 1 root root 19213626 Aug 27  2015 initrd.img-3.13.0-57-generic
-rw-r--r-- 1 root root 19215283 Aug 27  2015 initrd.img-3.13.0-62-generic
-rw-r--r-- 1 root root 19216233 May  3 20:33 initrd.img-3.13.0-68-generic
-rw-r--r-- 1 root root 19229950 May  3 20:47 initrd.img-3.13.0-85-generic
-rw-r--r-- 1 root root 19232595 Jun 27 13:01 initrd.img-3.13.0-88-generic
-rw-r--r-- 1 root root   176500 Mar 12  2014 memtest86+.bin
-rw-r--r-- 1 root root   178176 Mar 12  2014 memtest86+.elf
-rw-r--r-- 1 root root   178680 Mar 12  2014 memtest86+_multiboot.bin
-rw------- 1 root root  3390881 Jun 17  2015 System.map-3.13.0-55-generic
-rw------- 1 root root  3391581 Jun 19  2015 System.map-3.13.0-57-generic
-rw------- 1 root root  3392306 Aug 11  2015 System.map-3.13.0-62-generic
-rw------- 1 root root  3392383 Nov  6  2015 System.map-3.13.0-68-generic
-rw------- 1 root root  3394208 Mar 17  2016 System.map-3.13.0-85-generic
-rw-r--r-- 1 root root   165929 Jun  8 19:32 config-3.13.0-88-generic
drwxr-xr-x 3 root root     4096 Jun 27 13:01 extlinux
drwxr-xr-x 5 root root     4096 Jun 27 13:01 grub
-rw-r--r-- 1 root root 19213412 Jun 22  2015 initrd.img-3.13.0-55-generic
-rw-r--r-- 1 root root 19213626 Aug 27  2015 initrd.img-3.13.0-57-generic
-rw-r--r-- 1 root root 19215283 Aug 27  2015 initrd.img-3.13.0-62-generic
-rw-r--r-- 1 root root 19216233 May  3 20:33 initrd.img-3.13.0-68-generic
-rw-r--r-- 1 root root 19229950 May  3 20:47 initrd.img-3.13.0-85-generic
-rw-r--r-- 1 root root 19232595 Jun 27 13:01 initrd.img-3.13.0-88-generic
-rw-r--r-- 1 root root   176500 Mar 12  2014 memtest86+.bin
-rw-r--r-- 1 root root   178176 Mar 12  2014 memtest86+.elf
-rw-r--r-- 1 root root   178680 Mar 12  2014 memtest86+_multiboot.bin
-rw------- 1 root root  3390881 Jun 17  2015 System.map-3.13.0-55-generic
-rw------- 1 root root  3391581 Jun 19  2015 System.map-3.13.0-57-generic
-rw------- 1 root root  3392306 Aug 11  2015 System.map-3.13.0-62-generic
-rw------- 1 root root  3392383 Nov  6  2015 System.map-3.13.0-68-generic
-rw------- 1 root root  3394208 Mar 17  2016 System.map-3.13.0-85-generic
-rw------- 1 root root  3393683 Jun  8 19:32 System.map-3.13.0-88-generic
-rw------- 1 root root  5821984 Jun 17  2015 vmlinuz-3.13.0-55-generic
-rw------- 1 root root  5820800 Jun 19  2015 vmlinuz-3.13.0-57-generic
-rw------- 1 root root  5820896 Aug 11  2015 vmlinuz-3.13.0-62-generic
-rw------- 1 root root  5822400 Nov  6  2015 vmlinuz-3.13.0-68-generic
-rw------- 1 root root  5833568 Mar 17  2016 vmlinuz-3.13.0-85-generic
-rw------- 1 root root  5833888 Jun  8 19:32 vmlinuz-3.13.0-88-generic
admin1@csspc-base:/home/paul$ 

```
```
paul@csspc-base:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
udev            3.8G  4.0K  3.8G   1% /dev
tmpfs           774M  1.6M  772M   1% /run
/dev/sda6        24G   22G  713M  97% /
none            4.0K     0  4.0K   0% /sys/fs/cgroup
none            5.0M     0  5.0M   0% /run/lock
none            3.8G  1.2M  3.8G   1% /run/shm
none            100M   92K  100M   1% /run/user
/dev/sda7        32G   30G  125M 100% /home
/dev/sda8       145G  134G  3.3G  98% /mnt/data1

```
```
admin1@csspc-base:/home/paul$ sudo apt-get autoremove
[sudo] password for admin1: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  libhdb9-heimdal libkdc2-heimdal
0 upgraded, 0 newly installed, 2 to remove and 11 not upgraded.
After this operation, 440 kB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 410123 files and directories currently installed.)
Removing libkdc2-heimdal:amd64 (1.6~git20131207+dfsg-1ubuntu1.1) ...
Removing libhdb9-heimdal:amd64 (1.6~git20131207+dfsg-1ubuntu1.1) ...
Processing triggers for libc-bin (2.19-0ubuntu6.9) ...
admin1@csspc-base:/home/paul$ 

```
```
admin1@csspc-base:/home/paul$ df -h
Filesystem      Size  Used Avail Use% Mounted on
udev            3.8G  4.0K  3.8G   1% /dev
tmpfs           774M  1.6M  772M   1% /run
/dev/sda6        24G   22G  713M  97% /
none            4.0K     0  4.0K   0% /sys/fs/cgroup
none            5.0M     0  5.0M   0% /run/lock
none            3.8G  1.2M  3.8G   1% /run/shm
none            100M   92K  100M   1% /run/user
/dev/sda7        32G   30G  126M 100% /home
/dev/sda8       145G  134G  3.3G  98% /mnt/data1
admin1@csspc-base:/home/paul$
```

---

