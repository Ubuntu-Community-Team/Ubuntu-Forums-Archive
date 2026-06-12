---
title: "Kernel Not Updating"
date: 2014-10-08
forum: General Help
---

### Post by ktz84 on 2014-10-08
When doing updates I seem to be getting messages when there is a kernel update saying Error! Cannot locate dkms.conf. For instance tonight I'm sure the kernel showing was 3.13.0-37-generic however I got this message when I did a dist-upgrade however when I reboot and do uname -r I get 3.13.0-24-generic. How do I find out what the latest release through apt is on 14.04.1?

If I look is /boot I get this:

```
-rw-r--r-- 1 root root  1162227 Mar 24  2014 abi-3.13.0-19-generic-rw-r--r-- 1 root root  1158016 May  3 01:30 abi-3.13.0-24-generic
-rw-r--r-- 1 root root   165249 Mar 24  2014 config-3.13.0-19-generic
-rw-r--r-- 1 root root   165510 May  3 01:30 config-3.13.0-24-generic
drwxr-xr-x 6 root root     4096 Oct  8 22:28 grub
-rw-r--r-- 1 root root 18997401 Apr 19 12:17 initrd.img-3.13.0-19-generic
-rw-r--r-- 1 root root 25530564 Oct  6 21:26 initrd.img-3.13.0-24-generic
-rw-r--r-- 1 root root   176500 Mar 12  2014 memtest86+.bin
-rw-r--r-- 1 root root   178176 Mar 12  2014 memtest86+.elf
-rw-r--r-- 1 root root   178680 Mar 12  2014 memtest86+_multiboot.bin
-rw------- 1 root root  3369592 Mar 24  2014 System.map-3.13.0-19-generic
-rw------- 1 root root  3372643 May  3 01:30 System.map-3.13.0-24-generic
-rw-r--r-- 1 root root  5767040 Mar 29  2014 vmlinuz-3.13.0-19-generic
-rw------- 1 root root  5776416 May  3 01:30 vmlinuz-3.13.0-24-generic

```

so looking that it would seem that I 24 is the latest that's in there.

So am I on the latest and just imagining things :D

If I'm not how do I got about resolving any issues?

Thanks

---

### Post by ktz84 on 2014-10-08
OK. My virtualised ubuntu server 14.04.1 has just emailed me details of an upgraded kernel to 3.13.0-37-generic so I guess I'm not going mad :D

---

### Post by ktz84 on 2014-10-08
```
ls -l /var/lib/dkms
``` shows the following:

```
total 16-rw-r--r-- 1 root root    6 Jul  8  2008 dkms_dbversion
drwxr-xr-x 3 root root 4096 Oct  8 22:16 fglrx-updates
drwxr-xr-x 3 root root 4096 Oct  8 22:16 vboxguest
drwxr-xr-x 5 root root 4096 Sep  9 22:32 vboxhost
```

Don't if that helps any.

---

### Post by Impavidus on 2014-10-08
Could well be that 37 is the latest (I have 36 but I haven't upgraded this night yet), but it was clearly not installed on your system. You even skipped quite a lot of kernels, so you may have had the problem for a while. The output of```
sudo apt-get dist-upgrade
```may give some clues.

---

### Post by ktz84 on 2014-10-09
Impavids thanks for looking. That's the strange thing. When the dist-upgrade fails if I run it again it doesn't try to install it again so the output when I run it now looks like this:

```
Reading package lists... DoneBuilding dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 to upgrade, 0 to newly install, 0 to remove and 0 not to upgrade.

```

Not sure where to look for more info. There is nothing is /var/log/dist-upgrade. I can confirm that my system did indeed try to install 37 as it's in /var/log/dpkg.log and the relevant section shows this:

```
2014-10-08 22:15:55 install linux-headers-3.13.0-37:all <none> 3.13.0-37.642014-10-08 22:15:55 status half-installed linux-headers-3.13.0-37:all 3.13.0-37.64
2014-10-08 22:16:03 status unpacked linux-headers-3.13.0-37:all 3.13.0-37.64
2014-10-08 22:16:03 status unpacked linux-headers-3.13.0-37:all 3.13.0-37.64
2014-10-08 22:16:03 install linux-headers-3.13.0-37-generic:amd64 <none> 3.13.0-37.64
2014-10-08 22:16:03 status half-installed linux-headers-3.13.0-37-generic:amd64 3.13.0-37.64
2014-10-08 22:16:07 status unpacked linux-headers-3.13.0-37-generic:amd64 3.13.0-37.64
2014-10-08 22:16:07 status unpacked linux-headers-3.13.0-37-generic:amd64 3.13.0-37.64
2014-10-08 22:16:07 upgrade linux-headers-generic:amd64 3.13.0.36.43 3.13.0.37.44
2014-10-08 22:16:07 status half-configured linux-headers-generic:amd64 3.13.0.36.43
2014-10-08 22:16:07 status unpacked linux-headers-generic:amd64 3.13.0.36.43
2014-10-08 22:16:07 status half-installed linux-headers-generic:amd64 3.13.0.36.43
2014-10-08 22:16:07 status half-installed linux-headers-generic:amd64 3.13.0.36.43
2014-10-08 22:16:07 status unpacked linux-headers-generic:amd64 3.13.0.37.44
2014-10-08 22:16:07 status unpacked linux-headers-generic:amd64 3.13.0.37.44
2014-10-08 22:16:07 startup packages configure
2014-10-08 22:16:07 configure linux-headers-3.13.0-37:all 3.13.0-37.64 <none>
2014-10-08 22:16:07 status unpacked linux-headers-3.13.0-37:all 3.13.0-37.64
2014-10-08 22:16:07 status half-configured linux-headers-3.13.0-37:all 3.13.0-37.64
2014-10-08 22:16:07 status installed linux-headers-3.13.0-37:all 3.13.0-37.64
2014-10-08 22:16:07 configure linux-headers-3.13.0-37-generic:amd64 3.13.0-37.64 <none>
2014-10-08 22:16:07 status unpacked linux-headers-3.13.0-37-generic:amd64 3.13.0-37.64
2014-10-08 22:16:07 status half-configured linux-headers-3.13.0-37-generic:amd64 3.13.0-37.64
2014-10-08 22:16:51 status installed linux-headers-3.13.0-37-generic:amd64 3.13.0-37.64
2014-10-08 22:16:51 configure linux-headers-generic:amd64 3.13.0.37.44 <none>
2014-10-08 22:16:51 status unpacked linux-headers-generic:amd64 3.13.0.37.44
2014-10-08 22:16:51 status half-configured linux-headers-generic:amd64 3.13.0.37.44
2014-10-08 22:16:51 status installed linux-headers-generic:amd64 3.13.0.37.44
```

---

### Post by Impavidus on 2014-10-09
That's strange...

That log shows that the header packages have been installed. It says nothing about kernel images.

Just to see everything, what is the output of these commands:```
#I don't expect anything new from these
sudo apt-get update
sudo apt-get dist-upgrade

#Now to see the installed files
ls -l /usr/src
ls -l /boot

#And the list of packages your system thinks it has installed
dpkg --list linux-headers* linux-image*
```
I don't know about dkms, but I found these links:
Some background:
[https://help.ubuntu.com/community/DKMS](https://help.ubuntu.com/community/DKMS)
People with the same problem, somewhat older though:
[https://bbs.archlinux.org/viewtopic.php?id=151965](https://bbs.archlinux.org/viewtopic.php?id=151965)
[http://askubuntu.com/questions/227258/error-could-not-locate-dkms-conf-file](http://askubuntu.com/questions/227258/error-could-not-locate-dkms-conf-file)

---

### Post by ian-weisser on 2014-10-09
> **ktz84 said:**
> How do I find out what the latest release through apt is on 14.04.1?

Look at the version number of the linux-image-generic package.

Here's one way:
```
$ rmadison -u ubuntu linux-image-generic
 linux-image-generic | 2.6.32.21.22 | lucid            | amd64, i386
 linux-image-generic | 2.6.32.67.74 | lucid-security   | amd64, i386
 linux-image-generic | 2.6.32.67.74 | lucid-proposed   | amd64, i386
 linux-image-generic | 2.6.32.67.74 | lucid-updates    | amd64, i386
 linux-image-generic | 3.2.0.23.25  | precise          | amd64, i386
 linux-image-generic | 3.2.0.70.84  | precise-security | amd64, i386
 linux-image-generic | 3.2.0.70.84  | precise-proposed | amd64, i386
 linux-image-generic | 3.2.0.70.84  | precise-updates  | amd64, i386
 linux-image-generic | 3.13.0.24.28 | trusty           | amd64, arm64, armhf, i386, ppc64el
 linux-image-generic | 3.13.0.37.44 | trusty-security  | amd64, arm64, armhf, i386, ppc64el
 linux-image-generic | 3.13.0.37.44 | trusty-proposed  | amd64, arm64, armhf, i386, ppc64el
 linux-image-generic | 3.13.0.37.44 | trusty-updates   | amd64, arm64, armhf, i386, ppc64el
 linux-image-generic | 3.16.0.21.22 | utopic           | amd64, arm64, armhf, i386, ppc64el
```

If you're using 14.04, and you have trusty-updates enabled (like you should), then the current version would be 3.13.0-37.
The rmadison command is provided by the 'devscripts' package.

---

### Post by ktz84 on 2014-10-09
Impavidus there was no dist-upgrade when I ran it after doing an update. I did get a updated bash after doing and upgrade. The output from the other commands are:

```
ls -l /usr/srctotal 84
drwxr-xr-x  4 root root 4096 Apr 19 12:25 fglrx-updates-13.350.1
drwxr-xr-x 24 root root 4096 Mar 26  2014 linux-headers-3.13.0-19
drwxr-xr-x  7 root root 4096 Mar 26  2014 linux-headers-3.13.0-19-generic
drwxr-xr-x 24 root root 4096 May  6 07:49 linux-headers-3.13.0-24
drwxr-xr-x  7 root root 4096 May  6 07:49 linux-headers-3.13.0-24-generic
drwxr-xr-x 24 root root 4096 Jun  5 21:43 linux-headers-3.13.0-29
drwxr-xr-x  7 root root 4096 Jun  5 21:43 linux-headers-3.13.0-29-generic
drwxr-xr-x 24 root root 4096 Jul  5 18:47 linux-headers-3.13.0-30
drwxr-xr-x  7 root root 4096 Jul  5 18:47 linux-headers-3.13.0-30-generic
drwxr-xr-x 24 root root 4096 Jul 17 08:09 linux-headers-3.13.0-32
drwxr-xr-x  7 root root 4096 Jul 17 08:09 linux-headers-3.13.0-32-generic
drwxr-xr-x 24 root root 4096 Aug 12 07:15 linux-headers-3.13.0-33
drwxr-xr-x  7 root root 4096 Aug 12 07:15 linux-headers-3.13.0-33-generic
drwxr-xr-x 24 root root 4096 Aug 14 21:08 linux-headers-3.13.0-34
drwxr-xr-x  7 root root 4096 Aug 14 21:08 linux-headers-3.13.0-34-generic
drwxr-xr-x 24 root root 4096 Aug 29 22:58 linux-headers-3.13.0-35
drwxr-xr-x  7 root root 4096 Aug 29 22:58 linux-headers-3.13.0-35-generic
drwxr-xr-x 24 root root 4096 Sep 23 08:16 linux-headers-3.13.0-36
drwxr-xr-x  7 root root 4096 Sep 23 08:16 linux-headers-3.13.0-36-generic
drwxr-xr-x 24 root root 4096 Oct  8 22:16 linux-headers-3.13.0-37
drwxr-xr-x  7 root root 4096 Oct  8 22:16 linux-headers-3.13.0-37-generic
lrwxrwxrwx  1 root root   51 Jul  5 14:20 vboxguest-4.3.12 -> /opt/VBoxGuestAdditions-4.3.12/src/vboxguest-4.3.12
lrwxrwxrwx  1 root root   32 Sep  9 17:53 vboxhost-4.3.16 -> ../share/virtualbox/src/vboxhost

```

The output of:
```
 ls -l /boot
total 64484
-rw-r--r-- 1 root root  1162227 Mar 24  2014 abi-3.13.0-19-generic
-rw-r--r-- 1 root root  1158016 May  3 01:30 abi-3.13.0-24-generic
-rw-r--r-- 1 root root   165249 Mar 24  2014 config-3.13.0-19-generic
-rw-r--r-- 1 root root   165510 May  3 01:30 config-3.13.0-24-generic
drwxr-xr-x 6 root root     4096 Oct  8 22:28 grub
-rw-r--r-- 1 root root 18997401 Apr 19 12:17 initrd.img-3.13.0-19-generic
-rw-r--r-- 1 root root 25530564 Oct  6 21:26 initrd.img-3.13.0-24-generic
-rw-r--r-- 1 root root   176500 Mar 12  2014 memtest86+.bin
-rw-r--r-- 1 root root   178176 Mar 12  2014 memtest86+.elf
-rw-r--r-- 1 root root   178680 Mar 12  2014 memtest86+_multiboot.bin
-rw------- 1 root root  3369592 Mar 24  2014 System.map-3.13.0-19-generic
-rw------- 1 root root  3372643 May  3 01:30 System.map-3.13.0-24-generic
-rw-r--r-- 1 root root  5767040 Mar 29  2014 vmlinuz-3.13.0-19-generic
-rw------- 1 root root  5776416 May  3 01:30 vmlinuz-3.13.0-24-generic

```

The dpkg command doesn't show anything. Here's the output:

```
dpkg --list linux-headers* linux-image*
zsh: no matches found: linux-headers*

```

Thanks ian-weisser just checked out so good have for the future.

---

### Post by Impavidus on 2014-10-09
So you run the zsh shell instead of the bash shell and zsh gives an error when it cannot expand the *, where the bash shell would pass it to the command. So try```
dpkg --list 'linux-headers*' 'linux-image*'
```instead.

Still, I hope this thread is found by some specialist on dkms.

---

### Post by ktz84 on 2014-10-09
Hi. Sorry didn't realise that it was zsh that was having the problem in running that command. It's simple enough to temporarily switch to bash and I've run that original command.

The output is:

```
dpkg --list linux-headers* linux-image*Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                               Version                Architecture           Description
+++-==================================-======================-======================-==========================================================================
un  linux-headers                      <none>                 <none>                 (no description available)
un  linux-headers-3.0                  <none>                 <none>                 (no description available)
ii  linux-headers-3.13.0-19            3.13.0-19.40           all                    Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-19-generic    3.13.0-19.40           amd64                  Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-24            3.13.0-24.47           all                    Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-24-generic    3.13.0-24.47           amd64                  Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-29            3.13.0-29.53           all                    Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-29-generic    3.13.0-29.53           amd64                  Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-30            3.13.0-30.55           all                    Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-30-generic    3.13.0-30.55           amd64                  Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-32            3.13.0-32.57           all                    Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-32-generic    3.13.0-32.57           amd64                  Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-33            3.13.0-33.58           all                    Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-33-generic    3.13.0-33.58           amd64                  Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-34            3.13.0-34.60           all                    Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-34-generic    3.13.0-34.60           amd64                  Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-35            3.13.0-35.62           all                    Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-35-generic    3.13.0-35.62           amd64                  Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-36            3.13.0-36.63           all                    Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-36-generic    3.13.0-36.63           amd64                  Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
un  linux-headers-3.13.0-36-lowlatency <none>                 <none>                 (no description available)
ii  linux-headers-3.13.0-37            3.13.0-37.64           all                    Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-37-generic    3.13.0-37.64           amd64                  Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-generic              3.13.0.37.44           amd64                  Generic Linux kernel headers
un  linux-image                        <none>                 <none>                 (no description available)
un  linux-image-3.0                    <none>                 <none>                 (no description available)
ii  linux-image-3.13.0-19-generic      3.13.0-19.40           amd64                  Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-24-generic      3.13.0-24.47           amd64                  Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-36-generic      3.13.0-36.63           amd64                  Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-36-lowlatency   3.13.0-36.63           amd64                  Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-19-generi 3.13.0-19.40           amd64                  Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-24-generi 3.13.0-24.47           amd64                  Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP

```

---

### Post by ktz84 on 2014-10-09
OK progress. I installed linux-generic and it installed 0-37 as would be expected as this is the latest version. I did get the dkms message however that looks like a redherring at least as far kernel installation goes. I rebooted and when it tried to boot into my Ubuntu 14.04 install I got grub error saying that it could run 0-36-lowlatency. In advanced I could see 4 entries for 0-36 as well as the other older entries for 24. 24 was the latest version that would run for me. Back into Ubuntu 14.04 and run grub customizer and see no entries for 0-36 and it showing 0-37 as the default. Totally confused. Then remembered that I had installed in dual boot 14.10 Ubuntu Gnome so out and into Ubuntu Gnome 14.10 and sure enough in the grub.cfg those entries are there. So clearly I have two version of grub associated with each install with the Ubuntu Gnome 14.10 being the version that is actually running at boot.

Problem now is how I get both versions to use the same grub (preferrably the one on Ubuntu 14.04 as that has all the right entries for all operating systems).

---

### Post by ericius-tiscali on 2014-10-21
SOLVED
Hello,
i solved with

export GCC_EXEC_PREFIX=/usr/lib/gcc/i686-linux-gnu/4.8/
 
apt-get --reinstall install virtualbox-dkms

BY

---

