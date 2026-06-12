---
title: "when performing a command"
date: 2013-07-10
forum: General Help
---

### Post by adrianp918 on 2013-07-10
when i try this command 

apt-get -f install i get this error

Errors were encountered while processing:
 /var/cache/apt/archives/linux-image-3.2.0-49-generic-pae_3.2.0-49.75_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

i had to go this route cause i tried to run this command

apt-get install php5-gd

and it said this

The following packages have unmet dependencies:
 linux-image-generic-pae : Depends: linux-image-3.2.0-48-generic-pae but it is not going to be installed
 php5-gd : Depends: libgd2-xpm (>= 2.0.36~rc1~dfsg) but it is not going to be installed
           Depends: libt1-5 (>= 5.1.0) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

any help would be appreciated thank you

Adrian

---

### Post by adrianp918 on 2013-07-10
i should mention i am running ubuntu server and i tried to run this in command line, thank you

---

### Post by Habitual on 2013-07-10
> **adrianp918 said:**
> i should mention i am running ubuntu serverversion.........?

---

### Post by VMC on 2013-07-10
There are three commands that may solve your issue:

But first read the solution found [here]("http://www.maketecheasier.com/fix-ubuntu-update-errors/2011/12/16").

```

sudo rm -rf /var/lib/apt/lists/*
sudo apt-get clean
sudo apt-get update
```

---

### Post by adrianp918 on 2013-07-10
ok so i did all this and i still get the same error so i looked into it, and ran 
apt-get -f install and then i get this

(Reading database ... 339513 files and directories currently installed.)
Unpacking linux-image-3.2.0-49-generic-pae (from .../linux-image-3.2.0-49-generic-pae_3.2.0-49.75_i386.deb) ...
Done.
dpkg: error processing /var/cache/apt/archives/linux-image-3.2.0-49-generic-pae_3.2.0-49.75_i386.deb (--unpack):
 failed in write on buffer copy for backend dpkg-deb during `./boot/vmlinuz-3.2.0-49-generic-pae': No space left on device
No apport report written because the error message indicates a disk full error
                                                                              dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.2.0-49-generic-pae /boot/vmlinuz-3.2.0-49-generic-pae
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.2.0-49-generic-pae /boot/vmlinuz-3.2.0-49-generic-pae
Errors were encountered while processing:
 /var/cache/apt/archives/linux-image-3.2.0-49-generic-pae_3.2.0-49.75_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


so i looking into my drives and i have one that is 100% full, 



Mounted as   	                                             Type     	Location      	Used           	In use?        	Saved?   
/proc	Kernel Filesystem (proc)	proc	
Yes	Yes 
/ (Root filesystem)	             New Linux Native Filesystem (ext4)	LVM VG mapper, LV vm1--ubuntu-root	10%	Yes	Yes
/boot	                 Old Linux Native Filesystem (ext2)                   	Partition with ID efe13dc6-6564-4401-990c-3b9562f3d244	100 %	Yes	Yes


so from what i am seeing it is the /boot section of my drive that is totally full, anyway to fix this

i am running ubuntu server 12.04.1

---

### Post by grahammechanical on 2013-07-10
> so from what i am seeing it is the /boot section of my drive that is totally full, anyway to fix this

Yes, delete some of the older kernels from /boot. You must have /boot as a partition. When /boot is a folder on the / partition the size can increase.

Regards.

---

### Post by steeldriver on 2013-07-10
Do you have a bunch of old kernel images installed? that's usually how /boot gets full - you can either just list the contents of the boot dir (ls -l /boot) or run

```
dpkg -l | grep linux-image
```

to check - unfortunately you may have got to the point where you can't even use apt-get to UNinstall those kernels because of 0 free space; if that's the case then you may need to manually remove a couple of the oldest image files, afaik that shouldn't break anything provided you run 'apt-get purge' on the corresponding package(s) after to make sure the package database stays consistent - see [http://ubuntuforums.org/showthread.php?t=2098490&page=2](http://ubuntuforums.org/showthread.php?t=2098490&page=2)

---

### Post by adrianp918 on 2013-07-10
> root@vm1-ubuntu:~# dpkg -l | grep linux-image
rc  linux-image-3.0.0-12-generic-pae   3.0.0-12.20                  Linux kernel                      image for version 3.0.0 on x86
rc  linux-image-3.0.0-29-generic-pae   3.0.0-29.46                  Linux kernel                      image for version 3.0.0 on x86
ii  linux-image-3.0.0-30-generic-pae   3.0.0-30.47                  Linux kernel                      image for version 3.0.0 on x86
ii  linux-image-3.2.0-36-generic-pae   3.2.0-36.57                  Linux kernel                      image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-37-generic-pae   3.2.0-37.58                  Linux kernel                      image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-38-generic-pae   3.2.0-38.61                  Linux kernel                      image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-39-generic-pae   3.2.0-39.62                  Linux kernel                      image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-40-generic-pae   3.2.0-40.64                  Linux kernel                      image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-41-generic-pae   3.2.0-41.66                  Linux kernel                      image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-43-generic-pae   3.2.0-43.68                  Linux kernel                      image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-44-generic-pae   3.2.0-44.69                  Linux kernel                      image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-45-generic-pae   3.2.0-45.70                  Linux kernel                      image for version 3.2.0 on 32 bit x86 SMP
iU  linux-image-generic-pae            3.2.0.48.58                  Generic Linu                     x kernel image


This is what is in this file

can i manuall just delete them all?

---

### Post by Impavidus on 2013-07-11
```
sudo apt-get purge linux-image-<some version>
```
Uninstall all versions lower than 3.2.0-44.

---

