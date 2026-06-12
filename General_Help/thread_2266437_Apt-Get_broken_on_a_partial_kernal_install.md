---
title: "Apt-Get broken on a partial kernal install"
date: 2015-02-22
forum: General Help
---

### Post by Dustin_DuFault on 2015-02-22
I've searched this and other forums and am about at my wits end with my Ubuntu install. My apt-get has been stuck for a long time. I do not remember exactly what I did that borked it - but it seems to be stuck trying to remove kernels... but the files are missing and that's causing problems apt-get can't recover from.

As I mentioned I've run through every thread I could find on the topic with similar issues but mine won't budge. No matter which suggestions I try I always get the same error: dpkg: error processing package linux-image-extra-3.13.0-39-generic (--remove):

Here is the full output...

```
root@HalcyonWeb:/boot# apt-get install phpmyadmin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  dbconfig-common libjs-codemirror libjs-jquery-cookie libjs-jquery-event-drag
  libjs-jquery-metadata libjs-jquery-mousewheel libjs-jquery-tablesorter
  libjs-jquery-ui libmcrypt4 php-gettext php5-gd php5-mcrypt
Suggested packages:
  libjs-jquery-ui-docs libmcrypt-dev mcrypt
The following packages will be REMOVED:
  linux-image-extra-3.13.0-39-generic
The following NEW packages will be installed:
  dbconfig-common libjs-codemirror libjs-jquery-cookie libjs-jquery-event-drag
  libjs-jquery-metadata libjs-jquery-mousewheel libjs-jquery-tablesorter
  libjs-jquery-ui libmcrypt4 php-gettext php5-gd php5-mcrypt phpmyadmin
0 upgraded, 13 newly installed, 1 to remove and 0 not upgraded.
9 not fully installed or removed.
Need to get 5,574 kB of archives.
After this operation, 85.1 MB disk space will be freed.
Do you want to continue? [Y/n] 
Get:1 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main php5-gd i386 5.5.9+dfsg-1ubuntu4.6 [26.2 kB]
Get:2 http://us.archive.ubuntu.com/ubuntu/ trusty/main dbconfig-common all 1.8.47+nmu1 [468 kB]
Get:3 http://us.archive.ubuntu.com/ubuntu/ trusty/universe libjs-jquery-cookie all 8-2 [6,502 B]
Get:4 http://us.archive.ubuntu.com/ubuntu/ trusty/universe libjs-jquery-event-drag all 8-2 [11.2 kB]
Get:5 http://us.archive.ubuntu.com/ubuntu/ trusty/main libjs-jquery-metadata all 8-2 [6,856 B]
Get:6 http://us.archive.ubuntu.com/ubuntu/ trusty/universe libjs-jquery-mousewheel all 8-2 [7,076 B]
Get:7 http://us.archive.ubuntu.com/ubuntu/ trusty/main libjs-jquery-tablesorter all 8-2 [64.0 kB]
Get:8 http://us.archive.ubuntu.com/ubuntu/ trusty/universe libjs-jquery-ui all 1.10.1+dfsg-1 [458 kB]
Get:9 http://us.archive.ubuntu.com/ubuntu/ trusty/universe libmcrypt4 i386 2.5.8-3.1ubuntu1 [61.1 kB]
Get:10 http://us.archive.ubuntu.com/ubuntu/ trusty/universe php-gettext all 1.0.11-1 [17.2 kB]
Get:11 http://us.archive.ubuntu.com/ubuntu/ trusty/universe php5-mcrypt i386 5.4.6-0ubuntu5 [14.9 kB]
Get:12 http://us.archive.ubuntu.com/ubuntu/ trusty/universe libjs-codemirror all 2.23-1 [210 kB]
Get:13 http://us.archive.ubuntu.com/ubuntu/ trusty/universe phpmyadmin all 4:4.0.10-1 [4,224 kB]
Fetched 5,574 kB in 11s (502 kB/s)                                             
Preconfiguring packages ...
(Reading database ... 355670 files and directories currently installed.)
Removing linux-image-extra-3.13.0-39-generic (3.13.0-39.66) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.13.0-39-generic /boot/vmlinuz-3.13.0-39-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.13.0-39-generic /boot/vmlinuz-3.13.0-39-generic
update-initramfs: Generating /boot/initrd.img-3.13.0-39-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.13.0-39-generic /boot/vmlinuz-3.13.0-39-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.13.0-39-generic /boot/vmlinuz-3.13.0-39-generic
run-parts: executing /etc/kernel/postinst.d/zz-runlilo 3.13.0-39-generic /boot/vmlinuz-3.13.0-39-generic
Fatal: open /dev/disk/by-id/: Is a directory
run-parts: /etc/kernel/postinst.d/zz-runlilo exited with return code 1
dpkg: error processing package linux-image-extra-3.13.0-39-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
Errors were encountered while processing:
 linux-image-extra-3.13.0-39-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
```


Since I know that disk space in the /boot partition is known to cause similar issues, here is my output from df....

```
root@HalcyonWeb:/boot# df
Filesystem                      1K-blocks     Used Available Use% Mounted on
/dev/mapper/HalcyonWeb--vg-root 244848872 23574832 208813396  11% /
none                                    4        0         4   0% /sys/fs/cgroup
udev                               434048       12    434036   1% /dev
tmpfs                               89564     2060     87504   3% /run
none                                 5120        0      5120   0% /run/lock
none                               447808      236    447572   1% /run/shm
none                               102400       32    102368   1% /run/user
/dev/sda1                          240972   144145     84386  64% /boot
/dev/sr0                           146322   146322         0 100% /media/dustindufault/TurboTax 2014
```

My boot drive was actually much lower before I started working on this over the past couple of days, and it's ballooned from about 5% to the 64% you see here. Not sure why.

Your help is desperately needed & appreciated :D

-Dustin

---

### Post by ian-weisser on 2015-02-23
> **Dustin_DuFault said:**
> I've searched this and other forums and am about at my wits end with my Ubuntu install. My apt-get has been stuck for a long time. I do not remember exactly what I did that borked it - but it seems to be stuck trying to remove kernels... but the files are missing and that's causing problems apt-get can't recover from.
[...]
```
run-parts: executing /etc/kernel/postinst.d/zz-runlilo 3.13.0-39-generic /boot/vmlinuz-3.13.0-39-generic
** Fatal: open /dev/disk/by-id/: [COLOR=#ff0000]Is a directory[/COLOR]**
run-parts: /etc/kernel/postinst.d/zz-runlilo exited with return code 1
dpkg: error processing package linux-image-extra-3.13.0-39-generic (--remove):
```

zz-runlilo? Are you running lilo instead of grub?
Have you tried commenting out runlilo so the script doesn't fail? And then running runlilo separately afterwards? WARNING: Might break your bootloader.

Alternately, do you still have the kernel packages in your /var/apt/archive? If so, can you try reinstalling?
Alternately, do you still have the lilo packages in your /var/apt/archive? If so, can you try reinstalling?

> **Dustin_DuFault said:**
>  Since I know that disk space in the /boot partition is known to cause similar issues, here is my output from df....
A full /boot would cause an out-of-space error, not a script error.

---

### Post by Dustin_DuFault on 2015-02-23
Hmmm... I apologize for my inexperience, let me muddle through this...

-I'm not sure which bootloader I'm on --- but as far as I know it was the default when I installed Ubuntu.

-I don't appear to have a /var/apt/* directory at all :/

-I'm not sure how to edit the script that's being executed by apt... but will definitely try it with instructions! 

Thanks for helping out!

---

### Post by Dustin_DuFault on 2015-02-23
Ian - You fixed it, thank you.

I really think I am using grub (I'll have to check when I get home)... not sure how lilo got caught up in the mix here.

I decided to jump in on my own. I renamed the lilo file listed there to zz-runlilo.disabled and re-ran apt-get. All of my stuck kernel packages then deleted themselves and I am now able to install software with apt-get. I renamed the lilo packages back to their originals and everything seems to be working well again... I really can't thank you enough!! I was at my wits end trying to resolve this!

---

### Post by Dustin_DuFault on 2015-02-23
...aaand for completeness, I just survived a reboot. Still not 100% sure which bootloader I'm on...

---

### Post by ian-weisser on 2015-02-23
Fantastic to see you got it sorted.
Well done!

---

### Post by Dustin_DuFault on 2015-02-23
Thanks! 

It was definitely a downer earlier. It's been quite a while since I've had to re-format a system over something like this.... 

Good news is that I will now learn rsync to keep better backups so I'm not sweating bullets if I run into trouble again!

---

### Post by blackbeard2 on 2015-10-23
Dude, you are awesome!  I was scratching my head because my computer wouldn't update..an endless loop of it wouldn't update because it seemed initramfs files were broken, couldn't fix initramfs files because I couldn't update them....this fixed it!  Thanks a bunch!

---

