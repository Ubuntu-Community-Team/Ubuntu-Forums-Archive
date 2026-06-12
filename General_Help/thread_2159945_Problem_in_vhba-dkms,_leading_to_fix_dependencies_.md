---
title: "Problem in vhba-dkms, leading to fix dependencies failed due to no space left on devi"
date: 2013-07-05
forum: General Help
---

### Post by Macamba on 2013-07-05
Hi all,

I'm struggling with a problem, a bit. 

While updating my software I got an error. I was asked to report it, but that failed too. In the end all I got was the following window:
> Problem in vhba-dkms
This problem cannot be reported
This is not an official ubuntu package. Please remove any third party package and try again.

Next I tried to fix the installation.

```

macamba@Hermod:~$ sudo apt-get install --fix-broken
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  linux-headers-3.2.0-49
The following NEW packages will be installed:
  linux-headers-3.2.0-49
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
3 not fully installed or removed.
Need to get 0 B/11.7 MB of archives.
After this operation, 56.3 MB of additional disk space will be used.
Do you want to continue [Y/n]? 
(Reading database ... 505763 files and directories currently installed.)
Unpacking linux-headers-3.2.0-49 (from .../linux-headers-3.2.0-49_3.2.0-49.75_all.deb) ...
dpkg: error processing /var/cache/apt/archives/linux-headers-3.2.0-49_3.2.0-49.75_all.deb (--unpack):
 unable to create `/usr/src/linux-headers-3.2.0-49/arch/s390/include/asm/segment.h.dpkg-new' (while processing `./usr/src/linux-headers-3.2.0-49/arch/s390/include/asm/segment.h'): No space left on device
No apport report written because MaxReports is reached already
                                                              dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/linux-headers-3.2.0-49_3.2.0-49.75_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Because of the 'No space left on device' I thought to remove some old kernels
```

macamba@Hermod:~$ uname -r
3.2.0-48-generic
macamba@Hermod:~$ dpkg --list | grep linux-image
ii  linux-image-3.2.0-43-generic           3.2.0-43.68                                         Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-44-generic           3.2.0-44.69                                         Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-45-generic           3.2.0-45.70                                         Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-48-generic           3.2.0-48.74                                         Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-49-generic           3.2.0-49.75                                         Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-generic                    3.2.0.49.59                                         Generic Linux kernel image


macamba@Hermod:~$ sudo apt-get purge linux-image-3.2.0-43-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 linux-headers-3.2.0-49-generic : Depends: linux-headers-3.2.0-49 but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

macamba@Hermod:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  linux-headers-3.2.0-49
The following NEW packages will be installed:
  linux-headers-3.2.0-49
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
3 not fully installed or removed.
Need to get 0 B/11.7 MB of archives.
After this operation, 56.3 MB of additional disk space will be used.
Do you want to continue [Y/n]? 
(Reading database ... 505763 files and directories currently installed.)
Unpacking linux-headers-3.2.0-49 (from .../linux-headers-3.2.0-49_3.2.0-49.75_all.deb) ...
dpkg: error processing /var/cache/apt/archives/linux-headers-3.2.0-49_3.2.0-49.75_all.deb (--unpack):
 unable to create `/usr/src/linux-headers-3.2.0-49/arch/s390/include/asm/monwriter.h.dpkg-new' (while processing `./usr/src/linux-headers-3.2.0-49/arch/s390/include/asm/monwriter.h'): No space left on device
No apport report written because MaxReports is reached already
                                                              dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/linux-headers-3.2.0-49_3.2.0-49.75_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Still no space enough to clean up space (Catch 22 situation). Next I went to remove some old kernels by hand.
```
macamba@Hermod:~$ cd /boot
macamba@Hermod:~$ clear;ls -la
macamba@Hermod:~$ sudo rm config-3.2.0-43-generic
macamba@Hermod:~$ sudo rm config-3.2.0-44-generic
macamba@Hermod:~$ sudo rm vmlinuz-3.2.0-43-generic
macamba@Hermod:~$ sudo rm vmlinuz-3.2.0-44-generic
macamba@Hermod:~$ sudo rm initrd.img-3.2.0-43-generic
macamba@Hermod:~$ sudo rm initrd.img-3.2.0-44-generic
macamba@Hermod:~$ sudo rm System.map-3.2.0-43-generic
macamba@Hermod:~$ sudo rm System.map-3.2.0-44-generic

```

And still the apt-get -f install failed because of space problems.

So, what can I do now?

TIA,
Macamba

Edit:
I've been using [http://askubuntu.com/questions/171209/my-boot-partition-hit-100-and-now-i-cant-upgrade-cant-remove-old-kernels-to](http://askubuntu.com/questions/171209/my-boot-partition-hit-100-and-now-i-cant-upgrade-cant-remove-old-kernels-to) and other sources trying to get my problems solved.

---

### Post by Macamba on 2013-07-06
Well, still the same problem. I have packages with unmet dependencies, linux-headers-3.2.0-49-generic. If I perform a sudo apt-get -f install I get:
```

The following extra packages will be installed:
  linux-headers-3.2.0-49
The following NEW packages will be installed:
  linux-headers-3.2.0-49
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
3 not fully installed or removed.
Need to get 11.7 MB of archives.
After this operation, 56.3 MB of additional disk space will be used.

```

So, 56.3 MB of additional disk space will be used. How much space do I have?
```
df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda10      8.1G  6.6G  1.1G  87% /

```

So, that should work out, should it not? No, it should not. In my apt-get -f install I get:
```

...
Unpacking linux-headers-3.2.0-49 (from .../linux-headers-3.2.0-49_3.2.0-49.75_all.deb) ...
dpkg: error processing /var/cache/apt/archives/linux-headers-3.2.0-49_3.2.0-49.75_all.deb (--unpack):
 unable to create `/usr/src/linux-headers-3.2.0-49/arch/alpha/include/asm/bug.h.dpkg-new' (while processing `./usr/src/linux-headers-3.2.0-49/arch/alpha/include/asm/bug.h'): No space left on device
No apport report written because MaxReports is reached already
                                                              dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/linux-headers-3.2.0-49_3.2.0-49.75_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

I get a > No space left on device 
And that while I have **1.1G available!**

So, something else must be happening. 

I read somewhere to reinstall Ubuntu. Is that the way I should continue? Plug in the latest live CD, and do an install?

---

