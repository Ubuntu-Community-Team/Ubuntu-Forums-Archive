---
title: "No space left says gzip, but Disks say there are more."
date: 2017-05-25
forum: General Help
---

### Post by Azyx on 2017-05-25
I have a Lubuntu 16.04 on eee PC with a 16GB ssd-disk.

I use approx 1 GB for swap.


error.--> No space left.. message under.

But my lvm-volyme are 15GB, with 3,5BG free (76,7%) according to Disks

```
**[COLOR=#ff0000]gzip: stdout: No space left on device[/COLOR]**
E: mkinitramfs failure find 141 cpio 141 gzip 1
update-initramfs: failed for /boot/initrd.img-4.4.0-64-generic with 1.
dpkg: error processing package initramfs-tools (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 linux-image-extra-4.4.0-64-generic
 linux-image-4.4.0-78-generic
 linux-image-extra-4.4.0-78-generic
 linux-image-generic
 linux-firmware
 linux-image-4.4.0-72-generic
 linux-image-extra-4.4.0-72-generic
 linux-image-4.4.0-66-generic
 linux-generic
 linux-generic-lts-vivid
 linux-image-extra-4.4.0-66-generic
 initramfs-tools
Azyx@eeePC900:~$ 

```
Cheers

---

### Post by Impavidus on 2017-05-25
I think you ran out of space on your /boot partition. Most people don't have a /boot partition, but if you use lvm, you need one.

Run these commands and post the output so that we know what's going on:```
df -h
dpkg -l | grep linux-image
uname -r

```

---

### Post by Azyx on 2017-05-26
Thanks :) No :(  I did not make an /boot partition and the first time I use lvm.... Never use a boot-partition before lvm either, only / and /home.  

```
Azyx@eeePC900:~$ df -h
Filesystem                    Size  Used Avail Use% Mounted on
udev                          985M     0  985M   0% /dev
tmpfs                         201M  6,5M  195M   4% /run
/dev/mapper/lubuntu--vg-root   14G  8,7G  4,1G  69% /
tmpfs                        1003M     0 1003M   0% /dev/shm
tmpfs                         5,0M  4,0K  5,0M   1% /run/lock
tmpfs                        1003M     0 1003M   0% /sys/fs/cgroup
/dev/sda1                     236M  233M     0 100% /boot
cgmfs                         100K     0  100K   0% /run/cgmanager/fs
tmpfs                         201M   32K  201M   1% /run/user/1000
```

```
Azyx@eeePC900:~$ dpkg -l | grep linux-image
rc  linux-image-3.19.0-25-generic        3.19.0-25.26~14.04.1                       i386         Linux kernel image for version 3.19.0 on 32 bit x86 SMP
rc  linux-image-3.19.0-43-generic        3.19.0-43.49~14.04.1                       i386         Linux kernel image for version 3.19.0 on 32 bit x86 SMP
rc  linux-image-3.19.0-47-generic        3.19.0-47.53~14.04.1                       i386         Linux kernel image for version 3.19.0 on 32 bit x86 SMP
rc  linux-image-3.19.0-49-generic        3.19.0-49.55~14.04.1                       i386         Linux kernel image for version 3.19.0 on 32 bit x86 SMP
rc  linux-image-3.19.0-51-generic        3.19.0-51.58~14.04.1                       i386         Linux kernel image for version 3.19.0 on 32 bit x86 SMP
rc  linux-image-3.19.0-58-generic        3.19.0-58.64~14.04.1                       i386         Linux kernel image for version 3.19.0 on 32 bit x86 SMP
rc  linux-image-3.19.0-61-generic        3.19.0-61.69~14.04.1                       i386         Linux kernel image for version 3.19.0 on 32 bit x86 SMP
rc  linux-image-3.19.0-65-generic        3.19.0-65.73~14.04.1                       i386         Linux kernel image for version 3.19.0 on 32 bit x86 SMP
rc  linux-image-3.19.0-66-generic        3.19.0-66.74~14.04.1                       i386         Linux kernel image for version 3.19.0 on 32 bit x86 SMP
ii  linux-image-4.4.0-45-generic         4.4.0-45.66                                i386         Linux kernel image for version 4.4.0 on 32 bit x86 SMP
ii  linux-image-4.4.0-47-generic         4.4.0-47.68                                i386         Linux kernel image for version 4.4.0 on 32 bit x86 SMP
ii  linux-image-4.4.0-57-generic         4.4.0-57.78                                i386         Linux kernel image for version 4.4.0 on 32 bit x86 SMP
ii  linux-image-4.4.0-64-generic         4.4.0-64.85                                i386         Linux kernel image for version 4.4.0 on 32 bit x86 SMP
iF  linux-image-4.4.0-66-generic         4.4.0-66.87                                i386         Linux kernel image for version 4.4.0 on 32 bit x86 SMP
iF  linux-image-4.4.0-72-generic         4.4.0-72.93                                i386         Linux kernel image for version 4.4.0 on 32 bit x86 SMP
iF  linux-image-4.4.0-78-generic         4.4.0-78.99                                i386         Linux kernel image for version 4.4.0 on 32 bit x86 SMP
rc  linux-image-extra-3.19.0-25-generic  3.19.0-25.26~14.04.1                       i386         Linux kernel extra modules for version 3.19.0 on 32 bit x86 SMP
rc  linux-image-extra-3.19.0-43-generic  3.19.0-43.49~14.04.1                       i386         Linux kernel extra modules for version 3.19.0 on 32 bit x86 SMP
rc  linux-image-extra-3.19.0-47-generic  3.19.0-47.53~14.04.1                       i386         Linux kernel extra modules for version 3.19.0 on 32 bit x86 SMP
rc  linux-image-extra-3.19.0-49-generic  3.19.0-49.55~14.04.1                       i386         Linux kernel extra modules for version 3.19.0 on 32 bit x86 SMP
rc  linux-image-extra-3.19.0-51-generic  3.19.0-51.58~14.04.1                       i386         Linux kernel extra modules for version 3.19.0 on 32 bit x86 SMP
rc  linux-image-extra-3.19.0-58-generic  3.19.0-58.64~14.04.1                       i386         Linux kernel extra modules for version 3.19.0 on 32 bit x86 SMP
rc  linux-image-extra-3.19.0-61-generic  3.19.0-61.69~14.04.1                       i386         Linux kernel extra modules for version 3.19.0 on 32 bit x86 SMP
rc  linux-image-extra-3.19.0-65-generic  3.19.0-65.73~14.04.1                       i386         Linux kernel extra modules for version 3.19.0 on 32 bit x86 SMP
rc  linux-image-extra-3.19.0-66-generic  3.19.0-66.74~14.04.1                       i386         Linux kernel extra modules for version 3.19.0 on 32 bit x86 SMP
ii  linux-image-extra-4.4.0-45-generic   4.4.0-45.66                                i386         Linux kernel extra modules for version 4.4.0 on 32 bit x86 SMP
ii  linux-image-extra-4.4.0-47-generic   4.4.0-47.68                                i386         Linux kernel extra modules for version 4.4.0 on 32 bit x86 SMP
ii  linux-image-extra-4.4.0-57-generic   4.4.0-57.78                                i386         Linux kernel extra modules for version 4.4.0 on 32 bit x86 SMP
iF  linux-image-extra-4.4.0-64-generic   4.4.0-64.85                                i386         Linux kernel extra modules for version 4.4.0 on 32 bit x86 SMP
iU  linux-image-extra-4.4.0-66-generic   4.4.0-66.87                                i386         Linux kernel extra modules for version 4.4.0 on 32 bit x86 SMP
iU  linux-image-extra-4.4.0-72-generic   4.4.0-72.93                                i386         Linux kernel extra modules for version 4.4.0 on 32 bit x86 SMP
iU  linux-image-extra-4.4.0-78-generic   4.4.0-78.99                                i386         Linux kernel extra modules for version 4.4.0 on 32 bit x86 SMP
iU  linux-image-generic                  4.4.0.78.84                                i386         Generic Linux kernel image

```

```
Azyx@eeePC900:~$ uname -r
4.4.0-45-generic
```

/Cheers Azyx

---

### Post by Azyx on 2017-05-26
Seems like boot-partition is full...
/dev/sda1   236M  233M   0 100% /boot

---

### Post by Bashing-om on 2017-05-26
Azyx; Hello'

Try the easier way out here - likely, however, not to have the operating head room to work in.
```

sudo apt autoremove

```

Failing this we drop down to a lower level of package management .


[INDENT][INDENT]ain't nothing but thing
[/INDENT][/INDENT]

---

### Post by Impavidus on 2017-05-26
The Ubuntu installer automatically creates a /boot partition if you install on lvm because Ubuntu cannot boot from an lvm partition.

Let's see if dpkg is still willing to uninstall some old kernels. You're currently running 4.4.0-45, you want to get to 4.4.0-78, so you have to uninstall the ones inbetween.```
sudo dpkg --purge linux-image-extra-4.4.0-47-generic linux-image-4.4.0-47-generic
```That should remove one of them, if dpkg is happy with no breathing room at all. If it works, proceed with the other old 4.4 kernels (4.4.0-57 to 4.4.0-72). Next a simple```
sudo apt install -f
```should fix the problem.

If it doesn't work, you have to remove some of the /boot/initrd.img-4.4.0-* manually. Shouldn't be too bad, but show the result of```
ls /boot
```first.

---

### Post by Azyx on 2017-05-26
Thanks all :)

I have now manage to erase all imageexept *45 and *78 and memtest and other stuff by a combination of the proposed solutions above ;)

Is there a way to prevent this to happen in the future? This should not happen in a modern operating system, i think..

/Cheers

---

### Post by Bashing-om on 2017-05-26
Azyx; Hey .

> 
Is there a way to prevent this to happen in the future? This should not happen in a modern operating system, i think..


IMHO, a good system does not second guess what you want of the system.

One good means to accomplish auto autoremove is by enabling autoremove in /etc/apt/apt.conf.d/50unattended-upgrades

[INDENT][INDENT]more than one path to an end
[/INDENT][/INDENT]

---

### Post by ian-weisser on 2017-05-26
> **Azyx said:**
> Is there a way to prevent this to happen in the future? This should not happen in a modern operating system, i think..

That's right, and indeed it does not happen to the vast majority of Ubuntu users.
In 16.04 and newer, Ubuntu already autoremoves old kernels.

Either you have disabled or uninstalled unattended-upgrades, or you have somehow made your kernels ineligible for autoremoval.
You may have done either unintentionally.
Even then it wouldn't matter for years...unless, of course, you use LVM or encryption.

---

### Post by sp40140 on 2017-05-26
Along with old kernels, if you have a system which is on same install for a long time, you can delete old log files from /var/log. Compared to old kernels, they don't eat up much space, but for 16 gig drive, every little bit helps.

---

### Post by Azyx on 2017-05-26
Apt ignore '50unattended-upgrades.ucf-dist' because it has an invalid filename extension..... Read that it did not give any problems and it has not, on my other system, but on the other hand i do not use lvm there..

---

### Post by Azyx on 2017-05-26
Yes. I made an upgrade fron 14.04LTS to 16.04LTS, so there are a problem with 50unattended-upgrades and with lvm ubuntu only make a 255MB /boot partition. I have now added sudo apt autoremove to sudo apt update && sudo apt dist-upgrade in bash, I will se if that helps....

Cheers

---

### Post by Impavidus on 2017-05-27
> **sp40140 said:**
> Along with old kernels, if you have a system which is on same install for a long time, you can delete old log files from /var/log. Compared to old kernels, they don't eat up much space, but for 16 gig drive, every little bit helps.

Old log files, like those in /var/log/, should be handled by logrotate. Old logs should be automatically deleted after a week or a year or something inbetween. If you wish, you can change the behaviour of logrotate. Have a look at /etc/logrotate.conf, the files in /etc/logrotate.d/ and read **man logrotate**.

---

### Post by ian-weisser on 2017-05-27
> **Azyx said:**
> [T]here are a problem with 50unattended-upgrades
If you fix that, you may not need any other workarounds.

---

