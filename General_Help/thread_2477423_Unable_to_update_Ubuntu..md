---
title: "Unable to update Ubuntu."
date: 2022-07-24
forum: General Help
---

### Post by kwjorders on 2022-07-24
I am unable to update my dual booted Ubuntu desktop I get errors an error screen that says the package system is broken.  I have both disabled third party repositories.  Then I ran apt-get install &#8211;f but got the output below.
```
 dpkg: linux-image-5.15.0-27-generic: dependency problems, but removing anyway as you requested:
 linux-modules-5.15.0-27-generic depends on linux-image-5.15.0-27-generic | linux-image-unsigned-5.15.0-27-generic; however:
  Package linux-image-5.15.0-27-generic is to be removed.
  Package linux-image-unsigned-5.15.0-27-generic is not installed.

(Reading database ... 212471 files and directories currently installed.)
Removing linux-image-5.15.0-27-generic (5.15.0-27.28) ...
/etc/kernel/postrm.d/initramfs-tools:
update-initramfs: Deleting /boot/initrd.img-5.15.0-27-generic
/etc/kernel/postrm.d/zz-update-grub:
Sourcing file `/etc/default/grub'
Sourcing file `/etc/default/grub.d/init-select.cfg'
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-5.15.0-35-generic
Found initrd image: /boot/initrd.img-5.15.0-35-generic
Found linux image: /boot/vmlinuz-5.15.0-33-generic
Found initrd image: /boot/initrd.img-5.15.0-33-generic
Found memtest86+ image: /memtest86+.elf
Found memtest86+ image: /memtest86+.bin
Warning: os-prober will be executed to detect other bootable partitions.
Its output will be used to detect bootable binaries on them and create new boot entries.
Found Windows 10 on /dev/sda2
Found Windows 10 on /dev/sdc1
/etc/grub.d/bin/grubcfg_proxy: error while loading shared libraries: libcrypto.so.1.1: cannot open shared object file: No such file or directory
Found Windows 10 on /dev/sda2
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 127
dpkg: error processing package linux-image-5.15.0-27-generic (--remove):
 installed linux-image-5.15.0-27-generic package post-removal script subprocess returned error exit status 1
dpkg: too many errors, stopping
Errors were encountered while processing:
 linux-image-5.15.0-27-generic
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)
```
   
  I noticed that a lot of the lines refer to Grub which I am using to pick my operating system the other one being a Windows 10 install.  I have tried to delete the package but that does not work as well.
  -Thanks

---

### Post by deadflowr on 2022-07-24
Your issue seems to relate to grub-customizer.
See if this helps at all: [https://askubuntu.com/questions/1168054/how-to-fix-kernel-issue-after-upgrading-from-18-10-to-19-04]("https://askubuntu.com/questions/1168054/how-to-fix-kernel-issue-after-upgrading-from-18-10-to-19-04")

---

### Post by kwjorders on 2022-07-24
Looking at the other post I am unable to uninstall grub-customizer in the terminal with 
sudo apt-get purge grub-customizer

Looking around I was unable to install it either then try to uninstall it after that.
-Thanks

---

### Post by grahammechanical on 2022-07-25
> I noticed that a lot of the lines refer to Grub which I am using to pick my operating system

The  reason for those Grub entries is because a Linux kernel is being  removed. It is Linux 5.15.0-27-generic. I am guessing that the  update/upgrade processing is bringing in a new Linux kernel. The Linux  5.15.0-35-generic kernel and the update/upgrade process will always  remove an older kernel so that there are only two kernels on the system.  In turn the Grub configuration file is updated so as to present a newly  written Grub menu. That is why you are seeing those Grub entries. I  doubt that they are causing the problem.

Edit: This may help:

[https://www.tecmint.com/sub-process-usr-bin-dpkg-returned-an-error-in-ubuntu/](https://www.tecmint.com/sub-process-usr-bin-dpkg-returned-an-error-in-ubuntu/)

Regards

---

### Post by rsteinmetz70112 on 2022-07-26
> [COLOR=#000000]The Linux 5.15.0-35-generic kernel and the update/upgrade process will always remove an older kernel [/COLOR]

On my computers the update/upgrade does not remove old kernels. It is necessary to run "apt autoremove"

```
$ sudo apt update
$ sudo apt upgrade
$ sudo apt autoremove

```

---

### Post by #&amp;thj^% on 2022-07-26
> **rsteinmetz70112 said:**
> On my computers the update/upgrade does not remove old kernels. It is necessary to run "apt autoremove"

```
$ sudo apt update
$ sudo apt upgrade
$ sudo apt autoremove

```

How Odd, it should be as grahammechanical stated>
>  the update/upgrade process will always remove an older kernel _so that there are only two kernels on the system_
If a newer version is part of the upgrade.
IE:
```
$ find /boot/vmli*
/boot/vmlinuz
/boot/vmlinuz-5.15.0-25-generic
/boot/vmlinuz-5.15.0-41-generic
/boot/vmlinuz.old

```

---

### Post by kwjorders on 2022-07-30
I just went though all the commands in the link in grahammechanical post and the issue is still present.  I am unsure what was meant by 1fallen post under "If a newer version is part of the upgrade".
-Thanks

---

### Post by mattbach on 2022-08-01
will apt let you install software ?

---

### Post by kwjorders on 2022-08-01
I cannot install anything in the terminal.

---

### Post by #&amp;thj^% on 2022-08-01
Post back the return from:
```
sudo apt autoremove
```

---

### Post by kwjorders on 2022-08-01
~$ sudo apt autoremove
[sudo] password for: 
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
You might want to run 'apt --fix-broken install' to correct these.
The following packages have unmet dependencies:
E: Unmet dependencies. Try 'apt --fix-broken install' with no packages (or specify a solution).

---

### Post by #&amp;thj^% on 2022-08-01
Ok now I need to see this:
```
sudo apt --fix-broken install
```

---

### Post by grahammechanical on 2022-08-01
> I am unsure what was meant by 1fallen post under "If a newer version is part of the upgrade".

I was explaining the process that always or usually takes place when a new kernel is installed.

> the update/upgrade process will always  remove an older kernel so that there are only two kernels on the system.

@1fallen wanted to remove any misunderstanding. So he posted

> If a newer version is part of the upgrade.

I use Software Updater and when a new kernel is to be installed I am asked to authenticate. After the kernel is upgraded Software Updater asks for authentication to remove the oldest kernel. Older kernels are not removed if the kernel is not upgraded.

Regards

---

### Post by kwjorders on 2022-08-01
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  hwinfo libhd21 libpython2-stdlib libpython2.7-minimal libpython2.7-stdlib libx86emu3 python2 python2-minimal python2.7 python2.7-minimal
Use 'sudo apt autoremove' to remove them.
The following additional packages will be installed:
  linux-image-unsigned-5.15.0-27-generic
Suggested packages:
  fdutils linux-doc | linux-source-5.15.0 linux-tools linux-headers-5.15.0-27-generic linux-modules-extra-5.15.0-27-generic
The following packages will be REMOVED:
  linux-image-5.15.0-27-generic
The following NEW packages will be installed:
  linux-image-unsigned-5.15.0-27-generic
0 upgraded, 1 newly installed, 1 to remove and 231 not upgraded.
2 not fully installed or removed.
Need to get 0 B/11.2 MB of archives.
After this operation, 269 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
dpkg: warning: files list file for package 'linux-modules-5.15.0-27-generic' missing; assuming package has no files currently installed
(Reading database ... 211163 files and directories currently installed.)
Removing linux-image-5.15.0-27-generic (5.15.0-27.28) ...
/etc/kernel/postrm.d/initramfs-tools:
update-initramfs: Deleting /boot/initrd.img-5.15.0-27-generic
/etc/kernel/postrm.d/zz-update-grub:
Sourcing file `/etc/default/grub'
Sourcing file `/etc/default/grub.d/init-select.cfg'
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-5.15.0-35-generic
Found initrd image: /boot/initrd.img-5.15.0-35-generic
Found linux image: /boot/vmlinuz-5.15.0-33-generic
Found initrd image: /boot/initrd.img-5.15.0-33-generic
Found memtest86+ image: /memtest86+.elf
Found memtest86+ image: /memtest86+.bin
Warning: os-prober will be executed to detect other bootable partitions.
Its output will be used to detect bootable binaries on them and create new boot entries.
Found Windows 10 on /dev/sda2
Found Windows 10 on /dev/sdc1
/etc/grub.d/bin/grubcfg_proxy: error while loading shared libraries: libcrypto.so.1.1: cannot open shared object file: No such file or directory
Found Windows 10 on /dev/sda2
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 127
dpkg: error processing package linux-image-5.15.0-27-generic (--remove):
 installed linux-image-5.15.0-27-generic package post-removal script subprocess returned error exit status 1
dpkg: too many errors, stopping
Errors were encountered while processing:
 linux-image-5.15.0-27-generic
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by #&amp;thj^% on 2022-08-01
deadflowr is spot on>>>related to grub-customizer, now it gets to be a crap shoot from this point forward. (Be sure you have good back-ups in place first) 
I'm going to force a package in hopes to cure this, I've never done this myself, so a Strong Heads up this may not fix your issue, but i feel the risk is worth it for this problem.
We need to fix the missing libssl1.1 library manually. I provided the link at the bottom
run the following command to install libssl1.1:
```

sudo dpkg --install libssl1.1*.deb
```

After this the missing dependencies should be fixed and you can then clean out the linux-image if needed
[http://security.debian.org/debian-security/pool/updates/main/o/openssl/libssl1.1_1.1.0l-1~deb9u6_amd64.deb](http://security.debian.org/debian-security/pool/updates/main/o/openssl/libssl1.1_1.1.0l-1~deb9u6_amd64.deb) 
I have to leave for the nite but will check back....Good Luck

---

### Post by kwjorders on 2022-08-03
I attempted to use the command to fix the issue but it still doesn't work unless if there is some other way to fix it.  I will reinstall Ubuntu, I do not have much on the Ubunut partition most of my files are on my windows 10 partition.
-Thanks

---

