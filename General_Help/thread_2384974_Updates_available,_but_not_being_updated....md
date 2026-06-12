---
title: "Updates available, but not being updated..."
date: 2018-02-14
forum: General Help
---

### Post by Doulos1 on 2018-02-14
Server running on a 1-core VDS
Ubuntu 14.04

When I log in via SSH it shows I have 10 packages that have updates but nothing gets updated
> 10 packages can be updated.
10 updates are security updates.

But when I run apt-get update && apt-get upgrade...> The following packages have been kept back:
  linux-generic linux-headers-generic linux-headers-server linux-image-generic
  linux-image-server linux-server
0 upgraded, 0 newly installed, 0 to remove and 6 not upgraded.

I need to run 14.04 for now and am worried that security updates are available, but not being installed.

Suggestions?

Thanks in advance.

---

### Post by QIII on 2018-02-14
Hello!

That sounds like a job for

```
sudo apt-get dist-upgrade
```

if you think that the changes are appropriate.

If you want to see exactly what will be changed first, you can simulate the upgrade:

```
sudo apt-get -s dist-upgrade
```

dist-upgrade does not upgrade to a newer release of Ubuntu, so don't worry.

---

### Post by Impavidus on 2018-02-14
apt-get upgrade will only upgrade packages insofar that does not require installation of new packages. Instead of that, try```
apt-get dist-upgrade
```That should get you a new kernel.

---

### Post by Doulos1 on 2018-02-15
Thanks, I will try that.

---

### Post by Doulos1 on 2018-02-15
Here is what I get:
```
sudo apt-get dist-upgrade
Reading package lists... Done
Reading package lists... Done
Building dependency tree
Reading state information... Done
Calculating upgrade... Done
The following packages were automatically installed and are no longer required:
  libbz2-1.0:i386 libcap2:i386 libcgmanager0:i386 libdb5.3:i386 libdrm2:i386
  libjson-c2:i386 libjson0:i386 libncursesw5:i386 libudev1:i386
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
6 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] y
Setting up linux-image-3.13.0-141-generic (3.13.0-141.190) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
The link /initrd.img is a dangling linkto /boot/initrd.img-3.13.0-141-generic
vmlinuz(/boot/vmlinuz-3.13.0-141-generic
) points to /boot/vmlinuz-3.13.0-141-generic
 (/boot/vmlinuz-3.13.0-141-generic) -- doing nothing at /var/lib/dpkg/info/linux
-image-3.13.0-141-generic.postinst line 491.
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.13.0-141-generic
/boot/vmlinuz-3.13.0-141-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.13.0-141-generic /
boot/vmlinuz-3.13.0-141-generic
update-initramfs: Generating /boot/initrd.img-3.13.0-141-generic

gzip: stdout: No space left on device
E: mkinitramfs failure cpio 141 gzip 1
update-initramfs: failed for /boot/initrd.img-3.13.0-141-generic with 1.
run-parts: /etc/kernel/postinst.d/initramfs-tools exited with return code 1
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.13.
0-141-generic.postinst line 1025.
dpkg: error processing package linux-image-3.13.0-141-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-extra-3.13.0-141-
generic:
 linux-image-extra-3.13.0-141-generic depends on linux-image-3.13.0-141-generic;
 however:
  Package linux-image-3.13.0-141-generic is not configured yet.

dpkg: error processing package linux-image-extra-3.13.0-141-generic (--configure
):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup erro
r from a previous failure.
                          dpkg: dependency problems prevent configuration of lin
ux-image-generic:
 linux-image-generic depends on linux-image-3.13.0-141-generic; however:
  Package linux-image-3.13.0-141-generic is not configured yet.
 linux-image-generic depends on linux-image-extra-3.13.0-141-generic; however:
  Package linux-image-extra-3.13.0-141-generic is not configured yet.

dpkg: error processing package linux-image-generic (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup erro
r from a previous failure.
                          dpkg: dependency problems prevent configuration of lin
ux-generic:
 linux-generic depends on linux-image-generic (= 3.13.0.141.151); however:
  Package linux-image-generic is not configured yet.

dpkg: error processing package linux-generic (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency p
roblems prevent configuration of linux-image-server:
 linux-image-server depends on linux-image-generic (= 3.13.0.141.151); however:
  Package linux-image-generic is not configured yet.

dpkg: error processing package linux-image-server (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency p
roblems prevent configuration of linux-server:
 linux-server depends on linux-generic (= 3.13.0.141.151); however:
  Package linux-generic is not configured yet.

dpkg: error processing package linux-server (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              Errors were encoun
tered while processing:
 linux-image-3.13.0-141-generic
 linux-image-extra-3.13.0-141-generic
 linux-image-generic
 linux-generic
 linux-image-server
 linux-server
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by Impavidus on 2018-02-16
So you have a full /boot partition, which is an altogether different problem. There are many threads on that at these forums.

Find out which kernel you're running right now:```
uname -r
```
Then identify the old kernel packages you have:```
dpkg -l | grep linux-image
```
The old ones should have names like linux-image-3.13.0-nnn-generic or linux-image-extra-3.13.0-nnn-generic. Take a note of the exact version numbers in the package names. Keep the most recent one (3.13.0-141, not fully installed yet), the one before and the one you're currently running (probably the same). Then use dpkg to uninstall the others.```
sudo dpkg --purge linux-image-3.13.0-nnn-generic linux-image-extra-3.13.0-nnn-generic
```
Substitute the version numbers of the kernel packages you want to remove. Then run```
sudo apt-get install -f
```to complete installation of the partially installed packages.

---

### Post by Doulos1 on 2018-02-16
```
uname -r 3.13.0-117-generic
``````

dpkg -l | grep linux-image
ii  linux-image-3.13.0-117-generic        3.13.0-117.164     amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
iF  linux-image-3.13.0-141-generic        3.13.0-141.190     amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.2.0-23-generic          3.2.0-23.36     amd64        Linux kernel image for version 3.2.0 on 64 bit x86 SMP
rc  linux-image-3.2.0-24-generic          3.2.0-24.39     amd64        Linux kernel image for version 3.2.0 on 64 bit x86 SMP
rc  linux-image-3.2.0-38-generic          3.2.0-38.61     amd64        Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-58-generic          3.2.0-58.88     amd64        Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-117-generic  3.13.0-117.164     amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
iU  linux-image-extra-3.13.0-141-generic  3.13.0-141.190     amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
iU  linux-image-generic                   3.13.0.141.151     amd64        Generic Linux kernel image
iU  linux-image-server                    3.13.0.141.151     amd64        Transitional package.
```

I guess I am too noobish.  Could you please give me a complete example for removing one of my old kernels?

---

### Post by Yellow Pasque on 2018-02-16
Start here: [https://help.ubuntu.com/community/RemoveOldKernels](https://help.ubuntu.com/community/RemoveOldKernels)

---

### Post by Impavidus on 2018-02-16
Why didn't I know that help page?

You want to remove 3.2.0-58:```
sudo dpkg --purge linux-image-3.2.0-58-generic
```
Then it may be willing to fix the problem with```
sudo apt-get install -f
```

I'm surprised by the somewhat peculiar set of packages present on your system.

---

### Post by Doulos1 on 2018-02-16
I tried that and apt-get install -f fails with the same error with /boot at 84% used.  Here is the list of files using ```
sudo ls -l /boot
``` ```

total 60353
-rw-r--r-- 1 root root  1166834 Apr  7  2017 abi-3.13.0-117-generic
-rw-r--r-- 1 root root  1167513 Jan 19 08:32 abi-3.13.0-141-generic
-rw-r--r-- 1 root root   166050 Apr  7  2017 config-3.13.0-117-generic
-rw-r--r-- 1 root root   166080 Jan 19 08:32 config-3.13.0-141-generic
drwxr-xr-x 5 root root     7168 Feb 16 12:42 grub
-rw-r--r-- 1 root root 20026275 Feb  8 05:28 initrd.img-3.13.0-117-generic
-rw-r--r-- 1 root root 20035752 Feb 16 12:42 initrd.img-3.13.0-141-generic
drwx------ 2 root root    12288 Apr 26  2012 lost+found
-rw-r--r-- 1 root root   176500 Mar 12  2014 memtest86+.bin
-rw-r--r-- 1 root root   178176 Mar 12  2014 memtest86+.elf
-rw-r--r-- 1 root root   178680 Mar 12  2014 memtest86+_multiboot.bin
-rw------- 1 root root  3399741 Apr  7  2017 System.map-3.13.0-117-generic
-rw------- 1 root root  3404778 Jan 19 08:32 System.map-3.13.0-141-generic
-rw------- 1 root root  5850096 Apr  7  2017 vmlinuz-3.13.0-117-generic
-rw------- 1 root root  5856528 Jan 19 08:32 vmlinuz-3.13.0-141-generic
```

But ```
dpkg -S linux-image-extra*
``` still shows rc  linux-image-3.2.0-23-generic ```
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version      Architecture Description
+++-==============-============-============-=================================
un  linux-image    <none>       <none>       (no description available)
un  linux-image-3. <none>       <none>       (no description available)
ii  linux-image-3. 3.13.0-117.1 amd64        Linux kernel image for version 3.
ii  linux-image-3. 3.13.0-141.1 amd64        Linux kernel image for version 3.
rc  linux-image-3. 3.2.0-38.61  amd64        Linux kernel image for version 3.
ii  linux-image-ex 3.13.0-117.1 amd64        Linux kernel extra modules for ve
iF  linux-image-ex 3.13.0-141.1 amd64        Linux kernel extra modules for ve
iU  linux-image-ge 3.13.0.141.1 amd64        Generic Linux kernel image
iU  linux-image-se 3.13.0.141.1 amd64        Transitional package.
```

So I used  ```
sudo dpkg --purge linux-image-3.2.0-38-generic
``` and now this:```
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version      Architecture Description
+++-==============-============-============-=================================
un  linux-image    <none>       <none>       (no description available)
un  linux-image-3. <none>       <none>       (no description available)
ii  linux-image-3. 3.13.0-117.1 amd64        Linux kernel image for version 3.
ii  linux-image-3. 3.13.0-141.1 amd64        Linux kernel image for version 3.
ii  linux-image-ex 3.13.0-117.1 amd64        Linux kernel extra modules for ve
iF  linux-image-ex 3.13.0-141.1 amd64        Linux kernel extra modules for ve
iU  linux-image-ge 3.13.0.141.1 amd64        Generic Linux kernel image
iU  linux-image-se 3.13.0.141.1 amd64        Transitional package.
```

Following this I ran ```
sudo apt-get install -f
``` 
Still fails with the same errors.

```
sudo dpkg -l | grep linux-image  l
``````

ii  linux-image-3.13.0-117-generic        3.13.0-117.164 amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-141-generic        3.13.0-141.190 amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-117-generic  3.13.0-117.164 amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
iF  linux-image-extra-3.13.0-141-generic  3.13.0-141.190 amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
iU  linux-image-generic                   3.13.0.141.151 amd64        Generic Linux kernel image
iU  linux-image-server                    3.13.0.141.151 amd64        Transitional package.

```

---

### Post by Impavidus on 2018-02-17
When you run dpkg -l, could you first make the terminal window a bit larger, so that the output isn't truncated? And please use code tags, not quote tags. It's more readable.

Kernel packages listed with status rc are no concern. They take no disk space other than an entry in the package manager's database. Removing them just removes some clutter.

How large is your /boot partition? When I add up the files in your /boot partition I only come to 62 MB plus maybe a few MB in the /boot/grub directory. Are there any hidden files or directories, like a .Trash directory? Is there something in /boot/lost+found? Or is your /boot partition really tiny? Kernels are expanding, /boot partitions have to be bigger nowadays than 8 years ago. Expanding a /boot partition is often hard as you may have to shink other partition, which in turn tend to be LVM containers as that's the main reason why people have /boot partitions. Ideally, a /boot partition should be large enough to install a third kernel with two already installed or remove one with three installed. It should be at least 400 MB, which is still nothing on a modern hard drive.

---

### Post by vasa1 on 2018-02-17
> **Impavidus said:**
> ... And please use code tags, not quote tags. It's more readable.
...
PM sent to OP.

---

### Post by Doulos1 on 2018-02-17
> **Impavidus said:**
> When you run dpkg -l, could you first make the terminal window a bit larger, so that the output isn't truncated? And please use code tags, not quote tags. It's more readable. Sorry, I have been using Bitvise SSH Client which will not allow the terminal window to get any wider.  I will use putty from now on, I guess.

> **Impavidus said:**
> How large is your /boot partition? When I add up the files in your /boot partition I only come to 62 MB plus maybe a few MB in the /boot/grub directory. Are there any hidden files or directories, like a .Trash directory? Is there something in /boot/lost+found? Or is your /boot partition really tiny? Kernels are expanding, /boot partitions have to be bigger nowadays than 8 years ago. Expanding a /boot partition is often hard as you may have to shink other partition, which in turn tend to be LVM containers as that's the main reason why people have /boot partitions. Ideally, a /boot partition should be large enough to install a third kernel with two already installed or remove one with three installed. It should be at least 400 MB, which is still nothing on a modern hard drive.

```
#sudo df -h /boot
Filesystem      Size  Used Avail Use% Mounted on
/dev/xvda1       88M   68M   14M  84% /boot

```
```

Nothing is lost+found. No .Trash directory.
#cd /boot
#dir
abi-3.13.0-117-generic  config-3.13.0-117-generic  
grub                           
initrd.img-3.13.0-141-generic 
lost+found 
memtest86+.bin  
memtest86+_multiboot.bin       
System.map-3.13.0-141-generic  
vmlinuz-3.13.0-141-generic

```
This is on a 100GB VDS w/Ubuntu 14.04 that I use for off site backups and an older php script I use ...  I did not get to choose a file system at creation.  Still has 70Gb free, overall.

---

### Post by Impavidus on 2018-02-18
It may be possible to trick dpkg into believing the lines of the terminal are longer than they really are. I think it should be possible by setting the right environment variable, but I forgot which one. Piping the result through some other program or redirecting to a file works too:```
dpkg -l foo | cat
```

Your /boot partition is indeed tiny. There's just no room to make this work. Your initrd.img files are already small (20 MB, with my 4.13 kernels they're 50 MB). There's one trick you might try, but I've never done this myself, so I can't help with the details. You may be able to modify /etc/initramfs-tools/initramfs.conf to leave unneeded modules out of the init ram disk image, which should lead to a smaller initrd.img file, then hope it still boots. But really, that /boot partition is too small.

---

### Post by Doulos1 on 2018-02-18
Newer VDS installs with the same company no longer have such a small boot sector - but that doesn't help me any.  Thanks for your replies.

---

### Post by Doulos1 on 2018-02-19
I have been given the following advice but wanted to ask for other opinions on this ....

1. reboot server
2. manually delete all kernel files in the above list not relating to the current kernel (3.13.0-117)```
initrd.img-3.13.0-141-generic       System.map-3.13.0-141-generic  
vmlinuz-3.13.0-141-generic
```3. try upgrade again

I have tried all the suggestions up until now, but nothing has cleared enough space in /boot to finish the update.

---

### Post by Impavidus on 2018-02-20
Your linux-image-extra-3.13.0-141-generic is currently unpacked and half-configured. If you remove those files it will no longer be really unpacked. When trying the upgrade again, the package manager will attempt to configure the package and it will fail, as some files are missing. That will give an error that can only be fixed by reinstalling the package, bringing you back to where you are now.

No, I don't think that will work. The only possibilities I see are to make your initrd.img leaner or your /boot partition bigger. You could consider tweaking /etc/initramfs-tools/initramfs (see the manual using **man initramfs.conf**). I've never done that myself and don't know the risks, although I think that if done wrong it could make your system unbootable.

---

### Post by Doulos1 on 2018-02-20
Since, apparently, the only other option I have is to get another VDS with out a small separate /boot sector, I guess I will give resizing the partitions a try. Thanks for all your help and suggestions.

---

### Post by Doulos1 on 2018-03-03
What I decided to do was go with a fresh install of 16.04, PHP5.6, and mariadb. Then set up automatic purging of old kernels.  So far, so good.

Thanks for your help.

---

