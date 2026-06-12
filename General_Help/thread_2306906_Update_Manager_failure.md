---
title: "Update Manager failure"
date: 2015-12-20
forum: General Help
---

### Post by SageOfSmeg on 2015-12-20
I have a very old (1998) desktop PC that I leave running 24/7, on which I house a small PostgreSQL database.

Recently I tried running Update Manager but it keeps failing.
I have already taken a look at:
[http://askubuntu.com/questions/31667/what-does-no-apport-report-written-because-maxreports-is-reached-already-mean](http://askubuntu.com/questions/31667/what-does-no-apport-report-written-because-maxreports-is-reached-already-mean)


In terminal I have done as shown below.

```
gjd@gjdpc1:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  linux-headers-3.2.0-96 linux-headers-3.2.0-96-generic
The following NEW packages will be installed
  linux-headers-3.2.0-96 linux-headers-3.2.0-96-generic
0 to upgrade, 2 to newly install, 0 to remove and 0 not to upgrade.
2 not fully installed or removed.
Need to get 0 B/12.7 MB of archives.
After this operation, 67.8 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 250498 files and directories currently installed.)
Unpacking linux-headers-3.2.0-96 (from .../linux-headers-3.2.0-96_3.2.0-96.136_all.deb) ...
dpkg: error processing /var/cache/apt/archives/linux-headers-3.2.0-96_3.2.0-96.136_all.deb (--unpack):
 unable to create `/usr/src/linux-headers-3.2.0-96/arch/avr32/include/asm/timex.h.dpkg-new' (while processing `./usr/src/linux-headers-3.2.0-96/arch/avr32/include/asm/timex.h'): No space left on device
No apport report written because MaxReports has already been reached
                                                                    dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Unpacking linux-headers-3.2.0-96-generic (from .../linux-headers-3.2.0-96-generic_3.2.0-96.136_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/linux-headers-3.2.0-96-generic_3.2.0-96.136_i386.deb (--unpack):
 error creating symbolic link `./usr/src/linux-headers-3.2.0-96-generic/include/linux/mc6821.h': No space left on device
No apport report written because MaxReports has already been reached
                                                                    Errors were encountered while processing:
 /var/cache/apt/archives/linux-headers-3.2.0-96_3.2.0-96.136_all.deb
 /var/cache/apt/archives/linux-headers-3.2.0-96-generic_3.2.0-96.136_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
gjd@gjdpc1:~$
```

The key message I noticed was "No space left on device".
I have manually deleted some files from /var/log/syslog but it hasn't made much difference.
I am extremely limited in terms of hardware options and cannot currently increase storage.

I have also tried:
```
gjd@gjdpc1:~$ sudo dpkg --configure -a
dpkg: dependency problems prevent configuration of linux-headers-generic:
 linux-headers-generic depends on linux-headers-3.2.0-96-generic; however:
  Package linux-headers-3.2.0-96-generic is not installed.
dpkg: error processing linux-headers-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-headers-generic (= 3.2.0.96.112); however:
  Package linux-headers-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-headers-generic
 linux-generic
gjd@gjdpc1:~$

```

```
gjd@gjdpc1:~$ sudo ls -l /var/crash
total 0

```

I have considered manually removing old kernel images but have seen the warnings advising against it.
So I have tried:
```
sudo apt-get –f autoremove
```
but this failed as well.


```
gjd@gjdpc1:~$ sudo ls -lt /boot
total 70932
drwxr-xr-x 3 root root   12288 Dec 17 11:23 grub
-rw-r--r-- 1 root root 2213033 Dec 17 11:21 initrd.img-3.2.0-96-generic
-rw-r--r-- 1 root root  801436 Nov 30 23:14 abi-3.2.0-96-generic
-rw-r--r-- 1 root root  147821 Nov 30 23:14 config-3.2.0-96-generic
-rw------- 1 root root 2267375 Nov 30 23:14 System.map-3.2.0-96-generic
-rw------- 1 root root 4899584 Nov 30 23:14 vmlinuz-3.2.0-96-generic
-rw-r--r-- 1 root root 2213049 Nov 17 10:42 initrd.img-3.2.0-94-generic
-rw-r--r-- 1 root root  801367 Nov  6 19:53 abi-3.2.0-94-generic
-rw-r--r-- 1 root root  147821 Nov  6 19:53 config-3.2.0-94-generic
-rw------- 1 root root 2267336 Nov  6 19:53 System.map-3.2.0-94-generic
-rw------- 1 root root 4899136 Nov  6 19:53 vmlinuz-3.2.0-94-generic
-rw-r--r-- 1 root root 2212204 Aug  8 08:19 initrd.img-3.2.0-88-generic
-rw-r--r-- 1 root root  801170 Jul  6 23:20 abi-3.2.0-88-generic
-rw-r--r-- 1 root root  147799 Jul  6 23:20 config-3.2.0-88-generic
-rw------- 1 root root 2263334 Jul  6 23:20 System.map-3.2.0-88-generic
-rw------- 1 root root 4889952 Jul  6 23:20 vmlinuz-3.2.0-88-generic
-rw-r--r-- 1 root root 2212230 Jun 21 12:36 initrd.img-3.2.0-86-generic
-rw-r--r-- 1 root root 2212280 Jun 21 12:32 initrd.img-3.2.0-77-generic
-rw------- 1 root root 2263401 Jun 17  2015 System.map-3.2.0-86-generic
-rw-r--r-- 1 root root  801170 Jun 17  2015 abi-3.2.0-86-generic
-rw-r--r-- 1 root root  147799 Jun 17  2015 config-3.2.0-86-generic
-rw------- 1 root root 4889888 Jun 17  2015 vmlinuz-3.2.0-86-generic
-rw-r--r-- 1 root root  801107 Mar 10  2015 abi-3.2.0-77-generic
-rw-r--r-- 1 root root  147799 Mar 10  2015 config-3.2.0-77-generic
-rw------- 1 root root 2262516 Mar 10  2015 System.map-3.2.0-77-generic
-rw------- 1 root root 4886336 Mar 10  2015 vmlinuz-3.2.0-77-generic
-rw-r--r-- 1 root root 2214034 Oct  7  2014 initrd.img-3.2.0-69-generic
-rw-r--r-- 1 root root 2213395 Oct  7  2014 initrd.img-3.2.0-23-generic
-rw-r--r-- 1 root root  800473 Sep  2  2014 abi-3.2.0-69-generic
-rw-r--r-- 1 root root  147684 Sep  2  2014 config-3.2.0-69-generic
-rw------- 1 root root 2261768 Sep  2  2014 System.map-3.2.0-69-generic
-rw------- 1 root root 4884544 Sep  2  2014 vmlinuz-3.2.0-69-generic
-rw-r--r-- 1 root root  795572 Apr 11  2012 abi-3.2.0-23-generic
-rw-r--r-- 1 root root  147316 Apr 11  2012 config-3.2.0-23-generic
-rw------- 1 root root 2252691 Apr 11  2012 System.map-3.2.0-23-generic
-rw------- 1 root root 4864480 Apr 11  2012 vmlinuz-3.2.0-23-generic
-rw-r--r-- 1 root root  176764 Nov 27  2011 memtest86+.bin
-rw-r--r-- 1 root root  178944 Nov 27  2011 memtest86+_multiboot.bin
gjd@gjdpc1:~$

```

Any advice please?

--- 
Machine specs:
 Desktop: lubuntu 12.04 Precise, 12.04.5 LTS (GNU/Linux 3.2.0-96-generic i686)
 Kernel: 3.2.0-96-generic
 Pentium II 350 MHz
 768MB SDRAM
 8GB Hard Disks (2 x 4GB, Seagate ST34321A)
 Partitioning:
    /dev/sda5   ext4   4.3GB   /                 currently at 79% usage
    /dev/sdb5   ext4   2.2GB   /home             49% usage
    /dev/sdb6   ext4   1.0GB   /var              68% usage
    /dev/sdb7   ext4   1.1GB   linux-swap

---

### Post by coldraven on 2015-12-20
Have a look in /var/cache/apt/archives 
There is probably a copy of every package that has been installed. AFAIK it would do no harm to delete them all but you could back them up to an external device if you feel that you might need them later on.
There is a setting somewhere that stops these copies being saved but I cannot remember where it is. I'm at work* in a Windows environment at the moment so I can't check this.
There may also be a lot of stuff in /tmp that could be removed but maybe consult someone for guidance on this.
I had the same trouble with an Asus netbook that only had a 4GB SSD. I think that because /tmp was full it could not uncompress the update packages but I stand to be corrected on this.
Hopefully someone else with a bit more knowledge will join this discussion.

Edit: When I say that I'm at work I mean that I'm stuck in an office 900 miles from home with nothing much to do today except browse this forum :)

---

### Post by ian-weisser on 2015-12-20
Ah, good old [LP #1357093]("https://bugs.launchpad.net/bugs/1357093"). Please click the 'affects me too' link at the top of the bug report.

Freeing space using clean or autoclean is a good, simple way to temporarily fix the problem. Try it first.
A more complex way is to use dpkg to remove one or two old kernels.
The goal is simply to free enough space for apt to complete installing the kernels, so the package manager works again.

After apt works again, there are two ways to prevent the problem in the future:
1) Mark your wall calendar, and run 'autoremove' every month or so.
2) Use the unattended-upgrades package to regularly run autoremove for you. Edit the autoremove setting in /etc/apt/apt.conf.d/50unattended-upgrades from 'false' to 'true'

---

### Post by SageOfSmeg on 2015-12-21
Thanks for the tips.
 
I use autoclean and autoremove regularly but in this case it didn’t help.
 
Rather than just manually deleting old Linux kernel images/headers I went through the Synaptic Package Manager and removed the very old ones. That then enabled me to install the latest updates.
 
Now the system is up to date.

---

