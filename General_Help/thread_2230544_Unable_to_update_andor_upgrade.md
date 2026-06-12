---
title: "Unable to update and/or upgrade"
date: 2014-06-19
forum: General Help
---

### Post by Steve_Hess on 2014-06-19
Whether through update manager, or through terminal, I error out.

```
sudo apt-get update && sudo apt-get upgrade:

Fetched 1,024 kB in 20s (51.0 kB/s)
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 linux-headers-generic : Depends: linux-headers-3.13.0-29-generic but it is not installed
E: Unmet dependencies. Try using -f.

```

sudo apt-get -f install:

Unpacking linux-headers-3.13.0-29-generic (3.13.0-29.53) ...
dpkg: error processing archive /var/cache/apt/archives/linux-headers-3.13.0-29-generic_3.13.0-29.53_amd64.deb (--unpack):
 unable to create `/usr/src/linux-headers-3.13.0-29-generic/include/config/inotify/user.h.dpkg-new' (while processing `./usr/src/linux-headers-3.13.0-29-generic/include/config/inotify/user.h'): No space left on device
No apport report written because the error message indicates a disk full error
                                                                              dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/linux-headers-3.13.0-29-generic_3.13.0-29.53_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

When i open Ubuntu software center, I get the following text:

New software can't be installed because there is a problem with the software currently installed. Do you want to repair this problem now?
I'm given the option to 'repair' or 'cancel'. if I hit repair, I get the following error:

Package operation failed

the installation or removal of a software package failed.


(Reading database ... 417598 files and directories currently installed.)
Preparing to unpack .../linux-headers-3.13.0-29-generic_3.13.0-29.53_amd64.deb ...
Unpacking linux-headers-3.13.0-29-generic (3.13.0-29.53) ...
dpkg: error processing archive /var/cache/apt/archives/linux-headers-3.13.0-29-generic_3.13.0-29.53_amd64.deb (--unpack):
 unable to create `/usr/src/linux-headers-3.13.0-29-generic/include/config/bug.h.dpkg-new' (while processing `./usr/src/linux-headers-3.13.0-29-generic/include/config/bug.h'): No space left on device
No apport report written because the error message indicates a disk full error
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/linux-headers-3.13.0-29-generic_3.13.0-29.53_amd64.deb
Error in function: 
dpkg: dependency problems prevent configuration of linux-headers-generic:
 linux-headers-generic depends on linux-headers-3.13.0-29-generic; however:
  Package linux-headers-3.13.0-29-generic is not installed.


dpkg: error processing package linux-headers-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-headers-generic (= 3.13.0.29.35); however:
  Package linux-headers-generic is not configured yet.


dpkg: error processing package linux-generic (--configure):
 dependency problems - leaving unconfigured


The disk full error is odd, because none of my disks are full. I know this because when i run df, get the following:

Filesystem     1K-blocks      Used Available Use% Mounted on
/dev/sda6       36178648  13162504  21155332  39% /
none                   4         0         4   0% /sys/fs/cgroup
udev             3873544        12   3873532   1% /dev
tmpfs             776860      1384    775476   1% /run
none                5120         0      5120   0% /run/lock
none             3884300     25276   3859024   1% /run/shm
none              102400        68    102332   1% /run/user
/dev/sda2      124327968  42583252  81744716  35% /media/sudoer/48AEC994AEC97B48
/dev/sda3      807468724 121812996 685655728  16% /media/sudoer/New Volume




What do i do at this point. Thanks in advance. Also, I apologize for the formatting.

---

### Post by plucky on 2014-06-20
You might have run out of Inodes.

What does ```
df -i
``` show you?

---

### Post by Bucky Ball on 2014-06-20
Welcome. Run these three commands separately, ignoring any errors:

```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```

You need to upgrade to the -29 kernel and dist-upgrade should force that. Please enclose terminal output in [code] tags. I've given an example in your first post. Thanks.

---

