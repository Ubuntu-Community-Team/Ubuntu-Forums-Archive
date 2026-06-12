---
title: "Problem installing / remove / editing anything using apt-get"
date: 2013-09-06
forum: General Help
---

### Post by Ed_Ludlow on 2013-09-06
Hi there.

Returning to Ubuntu after a lengthy stay away: currently taking over management of a quite neglected virtual machine.  *cat /proc/version *shows:

```
Linux version 3.2.0-48-generic-pae (buildd@lamiak) (gcc version 4.6.3 (Ubuntu/Linaro 4.6.3-1ubuntu5) ) #74-Ubuntu SMP Thu Jun 6 20:05:01 UTC 2013
```

When trying to do anything with apt-get I'm getting:

```
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies.
 linux-generic-pae : Depends: linux-headers-generic-pae (= 3.2.0.51.61) but 3.2.0.52.62 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
```

Running *sudo-apt -f install*:

```
Reading package lists... Done
Building dependency tree
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  linux-headers-3.2.0-43-generic-pae linux-headers-3.2.0-41-generic-pae linux-headers-3.2.0-36-generic-pae linux-headers-3.2.0-40
  linux-headers-3.2.0-41 linux-headers-3.2.0-36 linux-headers-3.2.0-37 linux-headers-3.2.0-43 linux-headers-3.2.0-44
  linux-headers-3.2.0-39 linux-headers-3.2.0-45 linux-headers-3.2.0-44-generic-pae linux-headers-3.2.0-39-generic-pae
  linux-headers-3.2.0-37-generic-pae linux-headers-3.2.0-45-generic-pae linux-headers-3.2.0-40-generic-pae
  linux-image-3.2.0-25-generic-pae
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  linux-generic-pae linux-image-3.2.0-52-generic-pae linux-image-generic-pae
Suggested packages:
  fdutils linux-doc-3.2.0 linux-source-3.2.0 linux-tools
The following NEW packages will be installed
  linux-image-3.2.0-52-generic-pae
The following packages will be upgraded:
  linux-generic-pae linux-image-generic-pae
2 upgraded, 1 newly installed, 0 to remove and 91 not upgraded.
6 not fully installed or removed.
Need to get 0 B/38.3 MB of archives.
After this operation, 113 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 385763 files and directories currently installed.)
Unpacking linux-image-3.2.0-52-generic-pae (from .../linux-image-3.2.0-52-generic-pae_3.2.0-52.78_i386.deb) ...
Done.
dpkg: error processing /var/cache/apt/archives/linux-image-3.2.0-52-generic-pae_3.2.0-52.78_i386.deb (--unpack):
 failed in write on buffer copy for backend dpkg-deb during `./boot/vmlinuz-3.2.0-52-generic-pae': No space left on device
No apport report written because the error message indicates a disk full error
                                                                              dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.2.0-52-generic-pae /boot/vmlinuz-3.2.0-52-generic-pae
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.2.0-52-generic-pae /boot/vmlinuz-3.2.0-52-generic-pae
Errors were encountered while processing:
 /var/cache/apt/archives/linux-image-3.2.0-52-generic-pae_3.2.0-52.78_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

I'm thinking this is due to my /boot partition being full: *df* gives:

```

Filesystem                  1K-blocks    Used Available Use% Mounted on
/dev/mapper/vgubuntu-lvroot  14050376 4938820   8397828  38% /
udev                           505052       4    505048   1% /dev
none                           512624      16    512608   1% /tmp
tmpfs                          205052     248    204804   1% /run
none                             5120       0      5120   0% /run/lock
none                           512624       0    512624   0% /run/shm
/dev/sda1                      467367  463669         0 100% /boot
```

What should I be doing to solve things?  Any help appreciated, thanks.

---

### Post by bapoumba on 2013-09-06
```
No space left on device
No apport report written because the error message indicates a disk full error
```
Well yes, your boot partition is full.

Can you have a look and see if there is anything you can remove ? Not using a /boot partition, I cannot check what is in there.

---

### Post by howefield on 2013-09-06
Remove the older kernels, but keep the latest 2.

---

### Post by Ed_Ludlow on 2013-09-06
Thanks - will have a look at how to do that.

---

### Post by Ed_Ludlow on 2013-09-06
mmm, trying to run:

*sudo apt-get purge linux-image-3.2.0-23-generic-pae*

(the earliest unwanted kernel), I'm still getting:

```
Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies.
 linux-generic-pae : Depends: linux-headers-generic-pae (= 3.2.0.51.61) but 3.2.0.52.62 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
```

Not sure how I remove them then...

---

### Post by bluefrog on 2013-09-06
see my last post in [http://ubuntuforums.org/showthread.php?t=2172513](http://ubuntuforums.org/showthread.php?t=2172513)

---

### Post by Ed_Ludlow on 2013-09-06
Thanks.  Getting somewhere - I've now freed up a load of space in my /boot partition (only 47% used).

However, still getting the error when trying to use apt-get:

```
Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies.
 linux-generic-pae : Depends: linux-image-generic-pae (= 3.2.0.51.61) but 3.2.0.53.63 is to be installed
                     Depends: linux-headers-generic-pae (= 3.2.0.51.61) but 3.2.0.53.63 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).


```

So I run *sudo apt-get -f install*


```
Reading package lists... Done
Building dependency tree
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  linux-generic-pae
The following packages will be upgraded:
  linux-generic-pae
1 upgraded, 0 newly installed, 0 to remove and 91 not upgraded.
1 not fully installed or removed.
Need to get 0 B/1,726 B of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
dpkg: dependency problems prevent configuration of linux-generic-pae:
 linux-generic-pae depends on linux-image-generic-pae (= 3.2.0.51.61); however:
  Version of linux-image-generic-pae on system is 3.2.0.53.63.
 linux-generic-pae depends on linux-headers-generic-pae (= 3.2.0.51.61); however:
  Version of linux-headers-generic-pae on system is 3.2.0.53.63.
dpkg: error processing linux-generic-pae (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates it's a follow-up error from a previous failure.
                                                                                                            Errors were encountered while processing:
 linux-generic-pae
E: Sub-process /usr/bin/dpkg returned an error code (1)
```


Any suggestions? :(

---

### Post by vimer on 2013-09-06
Try remove the linux-generic image and reinstall it back later after that.

---

### Post by Ed_Ludlow on 2013-09-09
Thanks - call me thick, but how do I actually do that?  I can't remove using apt-get....and don't want to remove the wrong thing!

Thanks,
Ed

---

