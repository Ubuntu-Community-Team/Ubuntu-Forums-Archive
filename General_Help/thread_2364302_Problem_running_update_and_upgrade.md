---
title: "Problem running update and upgrade"
date: 2017-06-21
forum: General Help
---

### Post by satimis on 2017-06-21
Hi all,

Ubuntu 16.04

&#10219; sudo apt-get update ; sudo apt-get upgrade```

......
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

&#10219; sudo dpkg --configure -a```

Setting up linux-image-extra-4.4.0-81-generic (4.4.0-81.104) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-81-generic /boot/vmlinuz-4.4.0-81-generic
N: Ignoring file '50unattended-upgrades.ucf-dist' in directory '/etc/apt/apt.conf.d/' as it has an invalid filename extension
N: Ignoring file '50unattended-upgrades.ucf-dist' in directory '/etc/apt/apt.conf.d/' as it has an invalid filename extension
N: Ignoring file '50unattended-upgrades.ucf-dist' in directory '/etc/apt/apt.conf.d/' as it has an invalid filename extension
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-81-generic /boot/vmlinuz-4.4.0-81-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-81-generic

gzip: stdout: No space left on device
E: mkinitramfs failure cpio 141 gzip 1
update-initramfs: failed for /boot/initrd.img-4.4.0-81-generic with 1.
run-parts: /etc/kernel/postinst.d/initramfs-tools exited with return code 1
dpkg: error processing package linux-image-extra-4.4.0-81-generic (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-extra-4.4.0-81-generic; however:
  Package linux-image-extra-4.4.0-81-generic is not configured yet.

dpkg: error processing package linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 4.4.0.81.87); however:
  Package linux-image-generic is not configured yet.

dpkg: error processing package linux-generic (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-image-extra-4.4.0-81-generic
 linux-image-generic
 linux-generic

```

&#10219; sudo apt-get install -f```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
3 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up linux-image-extra-4.4.0-81-generic (4.4.0-81.104) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-81-generic /boot/vmlinuz-4.4.0-81-generic
N: Ignoring file '50unattended-upgrades.ucf-dist' in directory '/etc/apt/apt.conf.d/' as it has an invalid filename extension
N: Ignoring file '50unattended-upgrades.ucf-dist' in directory '/etc/apt/apt.conf.d/' as it has an invalid filename extension
N: Ignoring file '50unattended-upgrades.ucf-dist' in directory '/etc/apt/apt.conf.d/' as it has an invalid filename extension
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-81-generic /boot/vmlinuz-4.4.0-81-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-81-generic

gzip: stdout: No space left on device
E: mkinitramfs failure cpio 141 gzip 1
update-initramfs: failed for /boot/initrd.img-4.4.0-81-generic with 1.
run-parts: /etc/kernel/postinst.d/initramfs-tools exited with return code 1
dpkg: error processing package linux-image-extra-4.4.0-81-generic (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-extra-4.4.0-81-generic; however:
  Package linux-image-extra-4.4.0-81-generic is not configured yet.

dpkg: error processing package linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 4.4.0.81.87); however:
  Package linux-image-generic is not configured yet.

dpkg: error processing package linux-generic (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          No apport report written because the error message indicates its a followup error from a previous failure.
                                                    Errors were encountered while processing:
 linux-image-extra-4.4.0-81-generic
 linux-image-generic
 linux-generic
N: Ignoring file '50unattended-upgrades.ucf-dist' in directory '/etc/apt/apt.conf.d/' as it has an invalid filename extension
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

&#10219; cat /etc/apt/sources.list```

# deb cdrom:[Ubuntu 14.04 LTS _Trusty Tahr_ - Release amd64 (20140417)]/ trusty main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://hk.archive.ubuntu.com/ubuntu/ xenial main restricted
deb-src http://hk.archive.ubuntu.com/ubuntu/ xenial main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://hk.archive.ubuntu.com/ubuntu/ xenial-updates main restricted
deb-src http://hk.archive.ubuntu.com/ubuntu/ xenial-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://hk.archive.ubuntu.com/ubuntu/ xenial universe
deb-src http://hk.archive.ubuntu.com/ubuntu/ xenial universe
deb http://hk.archive.ubuntu.com/ubuntu/ xenial-updates universe
deb-src http://hk.archive.ubuntu.com/ubuntu/ xenial-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://hk.archive.ubuntu.com/ubuntu/ xenial multiverse
deb-src http://hk.archive.ubuntu.com/ubuntu/ xenial multiverse
deb http://hk.archive.ubuntu.com/ubuntu/ xenial-updates multiverse
deb-src http://hk.archive.ubuntu.com/ubuntu/ xenial-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://hk.archive.ubuntu.com/ubuntu/ xenial-backports main restricted universe multiverse
deb-src http://hk.archive.ubuntu.com/ubuntu/ xenial-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu xenial-security main restricted
deb-src http://security.ubuntu.com/ubuntu xenial-security main restricted
deb http://security.ubuntu.com/ubuntu xenial-security universe
deb-src http://security.ubuntu.com/ubuntu xenial-security universe
deb http://security.ubuntu.com/ubuntu xenial-security multiverse
deb-src http://security.ubuntu.com/ubuntu xenial-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu trusty partner
# deb-src http://archive.canonical.com/ubuntu trusty partner

```

Please advise how to fix the problem.  Thanks

Regards
satimis

---

### Post by Bashing-om on 2017-06-21
satimis; Hello again .

Ya got :
> 
gzip: stdout: No space left on device

try:
```

sudo apt autoremove

```
be aware if apt has no operating head room it will fail . and we will have to get the more aggressive to resolve .

[INDENT][INDENT]it's a thing
[/INDENT][/INDENT]

---

### Post by ajgreeny on 2017-06-21
Let me guess; you have a separate /boot partition, perhaps as a result of choosing encryption or LVM partitions at installation?

Bashing-om has already started down this road but to be more certain what your situation is at present please show us the output of command ```
df -h
``` followed by ```
dpkg -l | grep linux-image*
```

---

### Post by satimis on 2017-06-21
Hi all,

Thanks for your advice.

This is a VM (guest) of Oracle VirtualBox

Host - Ubuntu 16.04
VM - Ubuntu 16.04 upgraded from 14.04


&#10219; df -h```

Filesystem                   Size  Used Avail Use% Mounted on
udev                         980M     0  980M   0% /dev
tmpfs                        201M  3.7M  197M   2% /run
/dev/mapper/ubuntu--vg-root   38G  9.0G   27G  26% /
tmpfs                       1001M  1.6M  999M   1% /dev/shm
tmpfs                        5.0M  4.0K  5.0M   1% /run/lock
tmpfs                       1001M     0 1001M   0% /sys/fs/cgroup
/dev/sda1                    236M  201M   23M  90% /boot
cgmfs                        100K     0  100K   0% /run/cgmanager/fs
Transfer_Directory_PC1A      908G  696G  212G  77% /media/sf_Transfer_Directory_PC1A
tmpfs                        201M   60K  200M   1% /run/user/1000

```


&#10219; dpkg -l | grep linux-image*```

ii  linux-image-3.13.0-119-generic                        3.13.0-119.166                                amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-24-generic                         3.13.0-24.47                                  amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-27-generic                         3.13.0-27.50                                  amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-44-generic                         3.13.0-44.73                                  amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-46-generic                         3.13.0-46.79                                  amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-48-generic                         3.13.0-48.80                                  amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-78-generic                          4.4.0-78.99                                   amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-81-generic                          4.4.0-81.104                                  amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-119-generic                  3.13.0-119.166                                amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-24-generic                   3.13.0-24.47                                  amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-27-generic                   3.13.0-27.50                                  amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-44-generic                   3.13.0-44.73                                  amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-46-generic                   3.13.0-46.79                                  amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-48-generic                   3.13.0-48.80                                  amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-78-generic                    4.4.0-78.99                                   amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
iF  linux-image-extra-4.4.0-81-generic                    4.4.0-81.104                                  amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
iU  linux-image-generic                                   4.4.0.81.87                                   amd64        Generic Linux kernel image

```

There is plenty of space on the HD
Freespace: 227.5 GB

Edit-1
====
I have several VMs upgraded from Ubuntu 14.04 to 16.04 encountering some problem after upgrade


Edit-2
======

Just tested another VM, also upgraded from 14.04 to 16.04

&#10219; sudo apt-get update ; sudo apt-get ugrade```

Err:1 http://hk.archive.ubuntu.com/ubuntu xenial InRelease
  Temporary failure resolving 'hk.archive.ubuntu.com'
Err:2 http://security.ubuntu.com/ubuntu xenial-security InRelease
  Temporary failure resolving 'security.ubuntu.com'
Err:3 http://hk.archive.ubuntu.com/ubuntu xenial-updates InRelease
  Temporary failure resolving 'hk.archive.ubuntu.com'
Err:4 http://hk.archive.ubuntu.com/ubuntu xenial-backports InRelease
  Temporary failure resolving 'hk.archive.ubuntu.com'
Reading package lists... Done           
N: Ignoring file '50unattended-upgrades.ucf-dist' in directory '/etc/apt/apt.conf.d/' as it has an invalid filename extension
W: Failed to fetch http://hk.archive.ubuntu.com/ubuntu/dists/xenial/InRelease  Temporary failure resolving 'hk.archive.ubuntu.com'
W: Failed to fetch http://hk.archive.ubuntu.com/ubuntu/dists/xenial-updates/InRelease  Temporary failure resolving 'hk.archive.ubuntu.com'
W: Failed to fetch http://hk.archive.ubuntu.com/ubuntu/dists/xenial-backports/InRelease  Temporary failure resolving 'hk.archive.ubuntu.com'
W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/xenial-security/InRelease  Temporary failure resolving 'security.ubuntu.com'
W: Some index files failed to download. They have been ignored, or old ones used instead.
N: Ignoring file '50unattended-upgrades.ucf-dist' in directory '/etc/apt/apt.conf.d/' as it has an invalid filename extension
E: Invalid operation ugrade

```

But I suceeded to update/upgrade it running "Software-updater"


Regards
satimis

---

### Post by canadianbill007 on 2017-06-22
Would also suggest running ...

sudo autoremove -y 

after upgrading.

---

### Post by satimis on 2017-06-22
> **wheckadon said:**
> Would also suggest running ...

sudo autoremove -y 

after upgrading.
Hi,

Thanks for your advice.

All VMs upgraded from Ubuntu 14.04 to 16.04 have been updated by running "Software Updater".  They are now up-to-date.  I'll try your suggestion later.

I suppose the command suggested should be "sudo apt autoremove -y" ?

Regards
satimis

---

### Post by Impavidus on 2017-06-22
Yes, sudo apt autoremove -y will remove unneeded packages. However, take care. -y means "just do it and don't ask further questions". Which means that apt may remove packages that you'd have liked to keep and weren't aware of that they were autoremovable. So, generally, I wouldn't recommend using autoremove -y. Better to get a chance to see the list of packages to be removed and abort if you wish.

---

### Post by satimis on 2017-06-22
Hi all,

Something strange happened on this VM, also upgraded from Ubuntu 14.04 to 16.06

On running "Software Updater" it displayed following notice finally"```

the software on this computer is up to date

```

On terminal run;
&#10219; sudo apt-get update ; sudo apt-get upgrade
```

Hit:1 http://hk.archive.ubuntu.com/ubuntu xenial InRelease
Hit:2 http://hk.archive.ubuntu.com/ubuntu xenial-updates InRelease
Hit:3 http://hk.archive.ubuntu.com/ubuntu xenial-backports InRelease
Get:4 http://security.ubuntu.com/ubuntu xenial-security InRelease [102 kB]
Fetched 102 kB in 6s (16.2 kB/s)                                               
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
3 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] 

```

Do you want to continue? [Y/n] y```

Setting up linux-image-extra-4.4.0-81-generic (4.4.0-81.104) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-81-generic /boot/vmlinuz-4.4.0-81-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-81-generic /boot/vmlinuz-4.4.0-81-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-81-generic

gzip: stdout: No space left on device
E: mkinitramfs failure cpio 141 gzip 1
update-initramfs: failed for /boot/initrd.img-4.4.0-81-generic with 1.
run-parts: /etc/kernel/postinst.d/initramfs-tools exited with return code 1
dpkg: error processing package linux-image-extra-4.4.0-81-generic (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-extra-4.4.0-81-generic; however:
  Package linux-image-extra-4.4.0-81-generic is not configured yet.

dpkg: error processing package linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 4.4.0.81.87); however:
  Package linux-image-generic is not configured yet.

dpkg: error processing package linux-generic (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          No apport report written because the error message indicates its a followup error from a previous failure.
                                                    Errors were encountered while processing:
 linux-image-extra-4.4.0-81-generic
 linux-image-generic
 linux-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Then I run;
&#10219; sudo apt-get autoremove```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
3 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up linux-image-extra-4.4.0-81-generic (4.4.0-81.104) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-81-generic /boot/vmlinuz-4.4.0-81-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-81-generic /boot/vmlinuz-4.4.0-81-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-81-generic

gzip: stdout: No space left on device
E: mkinitramfs failure cpio 141 gzip 1
update-initramfs: failed for /boot/initrd.img-4.4.0-81-generic with 1.
run-parts: /etc/kernel/postinst.d/initramfs-tools exited with return code 1
dpkg: error processing package linux-image-extra-4.4.0-81-generic (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-extra-4.4.0-81-generic; however:
  Package linux-image-extra-4.4.0-81-generic is not configured yet.

dpkg: error processing package linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 4.4.0.81.87); however:
  Package linux-image-generic is not configured yet.

dpkg: error processing package linux-generic (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          No apport report written because the error message indicates its a followup error from a previous failure.
                                                    Errors were encountered while processing:
 linux-image-extra-4.4.0-81-generic
 linux-image-generic
 linux-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Please advise how to fix the problem?

Thanks

Regards
satimis

---

### Post by ajgreeny on 2017-06-22
In post #4 you show```
/dev/sda1                    236M  201M   23M  90% /boot
``` which suggests, as I thought that you are running out of space in the /boot partition of this VM.  You have two kernels of the original 3.13.0 series and two of the 4.4.0 series which is bound to overfill the /boot partition that you have.

You can also forget about the physical disk being 227.5 GB available as that has nothing to do with this specific VM which looks to be 38GB according to the output ```
/dev/mapper/ubuntu--vg-root   38G  9.0G   27G  26% /
```

Let's try dpkg to get rid of the old 3.13.0-series first with command ```
sudo dpkg -P linux-image-extra-3.13.0-119-generic linux-image-extra-3.13.0-24-generic
sudo dpkg -P linux-image-3.13.0-119-generic linux-image-3.13.0-24-generic
```then try running ```
sudo apt-get autoremove --purge
``` to get rid of any remaining dross in the system.

---

### Post by satimis on 2017-06-22
> **ajgreeny said:**
> In post #4 you show```
/dev/sda1                    236M  201M   23M  90% /boot
``` which suggests, as I thought that you are running out of space in the /boot partition of this VM.  You have two kernels of the original 3.13.0 series and two of the 4.4.0 series which is bound to overfill the /boot partition that you have.

You can also forget about the physical disk being 227.5 GB available as that has nothing to do with this specific VM which looks to be 38GB according to the output ```
/dev/mapper/ubuntu--vg-root   38G  9.0G   27G  26% /
```

Let's try dpkg to get rid of the old 3.13.0-series first with command ```
sudo dpkg -P linux-image-extra-3.13.0-119-generic linux-image-extra-3.13.0-24-generic
sudo dpkg -P linux-image-3.13.0-119-generic linux-image-3.13.0-24-generic
```then try running ```
sudo apt-get autoremove --purge
``` to get rid of any remaining dross in the system.

Hi,

Lot of thanks for your advice.  Performed following steps.

&#10219; sudo dpkg -P linux-image-extra-3.13.0-119-generic linux-image-extra-3.13.0-24-generic```

(Reading database ... 292195 files and directories currently installed.)
Removing linux-image-extra-3.13.0-119-generic (3.13.0-119.166) ...
Purging configuration files for linux-image-extra-3.13.0-119-generic (3.13.0-119.166) ...
Removing linux-image-extra-3.13.0-24-generic (3.13.0-24.47) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.13.0-24-generic /boot/vmlinuz-3.13.0-24-generic
update-initramfs: Deleting /boot/initrd.img-3.13.0-24-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.13.0-24-generic /boot/vmlinuz-3.13.0-24-generic
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-4.4.0-81-generic
Found initrd image: /boot/initrd.img-4.4.0-81-generic
Found linux image: /boot/vmlinuz-4.4.0-78-generic
Found initrd image: /boot/initrd.img-4.4.0-78-generic
Found linux image: /boot/vmlinuz-3.13.0-29-generic
Found initrd image: /boot/initrd.img-3.13.0-29-generic
Found linux image: /boot/vmlinuz-3.13.0-24-generic
Found memtest86+ image: /memtest86+.elf
Found memtest86+ image: /memtest86+.bin
done
Purging configuration files for linux-image-extra-3.13.0-24-generic (3.13.0-24.47) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.13.0-24-generic /boot/vmlinuz-3.13.0-24-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.13.0-24-generic /boot/vmlinuz-3.13.0-24-generic

```

&#10219; sudo dpkg -P linux-image-3.13.0-119-generic linux-image-3.13.0-24-generic```

(Reading database ... 288285 files and directories currently installed.)
Removing linux-image-3.13.0-119-generic (3.13.0-119.166) ...
Purging configuration files for linux-image-3.13.0-119-generic (3.13.0-119.166) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.13.0-119-generic /boot/vmlinuz-3.13.0-119-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.13.0-119-generic /boot/vmlinuz-3.13.0-119-generic
Removing linux-image-3.13.0-24-generic (3.13.0-24.47) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.13.0-24-generic /boot/vmlinuz-3.13.0-24-generic
update-initramfs: Deleting /boot/initrd.img-3.13.0-24-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.13.0-24-generic /boot/vmlinuz-3.13.0-24-generic
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-4.4.0-81-generic
Found initrd image: /boot/initrd.img-4.4.0-81-generic
Found linux image: /boot/vmlinuz-4.4.0-78-generic
Found initrd image: /boot/initrd.img-4.4.0-78-generic
Found linux image: /boot/vmlinuz-3.13.0-29-generic
Found initrd image: /boot/initrd.img-3.13.0-29-generic
Found memtest86+ image: /memtest86+.elf
Found memtest86+ image: /memtest86+.bin
done
Purging configuration files for linux-image-3.13.0-24-generic (3.13.0-24.47) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.13.0-24-generic /boot/vmlinuz-3.13.0-24-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.13.0-24-generic /boot/vmlinuz-3.13.0-24-generic

```

&#10219; sudo apt-get autoremove --purge```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
3 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up linux-image-extra-4.4.0-81-generic (4.4.0-81.104) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-81-generic /boot/vmlinuz-4.4.0-81-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-81-generic /boot/vmlinuz-4.4.0-81-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-81-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 4.4.0-81-generic /boot/vmlinuz-4.4.0-81-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 4.4.0-81-generic /boot/vmlinuz-4.4.0-81-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 4.4.0-81-generic /boot/vmlinuz-4.4.0-81-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 4.4.0-81-generic /boot/vmlinuz-4.4.0-81-generic
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-4.4.0-81-generic
Found initrd image: /boot/initrd.img-4.4.0-81-generic
Found linux image: /boot/vmlinuz-4.4.0-78-generic
Found initrd image: /boot/initrd.img-4.4.0-78-generic
Found linux image: /boot/vmlinuz-3.13.0-29-generic
Found initrd image: /boot/initrd.img-3.13.0-29-generic
Found memtest86+ image: /memtest86+.elf
Found memtest86+ image: /memtest86+.bin
done
Setting up linux-image-generic (4.4.0.81.87) ...
Setting up linux-generic (4.4.0.81.87) ...

```

Rebooted VM

Ran "Software Updater"```

The software on this computer is up to date

```

On terminal:
&#10219; sudo apt-get update ; sudo apt-get upgrade```

[sudo] password for satimis: 
Get:1 http://security.ubuntu.com/ubuntu xenial-security InRelease [102 kB]
Hit:2 http://hk.archive.ubuntu.com/ubuntu xenial InRelease               
Hit:3 http://hk.archive.ubuntu.com/ubuntu xenial-updates InRelease
Hit:4 http://hk.archive.ubuntu.com/ubuntu xenial-backports InRelease
Fetched 102 kB in 5s (19.1 kB/s)                  
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```


Still I can't resolve that this VM was cloned on another VM installed on Ubuntu 14.04 ISO download on website.  IIRC I didn't fixed the storage size of this original VM nor that of this cloned VM, allowing it to expand.  Whether the boot partition is permanently fixed and can't extend its storage size even though there is plenty of space on the HD?

Most the time I prefer clean installation.  It is because this VM is the local websites of those running on Godaddy server I'm compelled to upgrade it to Ubuntu 16.04

Thanks again for your help.

Regards
satimis

---

