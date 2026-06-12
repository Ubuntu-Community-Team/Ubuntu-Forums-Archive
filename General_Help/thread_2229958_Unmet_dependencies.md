---
title: "Unmet dependencies"
date: 2014-06-16
forum: General Help
---

### Post by Jason_Canup on 2014-06-16
Hi all-

Im having an issue installing anything...apps, updates, everything.  My /boot partition is full and complaining about errors whenever I try to install updates or apps.

The error message is:

```
You might want to run 'apt-get -f install' to correct these:The following packages have unmet dependencies:
 gparted : Depends: libgtkmm-2.4-1c2a (>= 1:2.24.0) but it is not going to be installed
 linux-generic : Depends: linux-headers-generic (= 3.2.0.61.72) but 3.2.0.64.76 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
```

So, I run sudo apt-get -f install and get this:

```
dpkg: error processing /var/cache/apt/archives/linux-image-3.2.0-64-generic_3.2.0-64.97_amd64.deb (--unpack): failed in write on buffer copy for backend dpkg-deb during `./boot/vmlinuz-3.2.0-64-generic': No space left on device
No apport report written because the error message indicates a disk full error
                                                                              dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.2.0-64-generic /boot/vmlinuz-3.2.0-64-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.2.0-64-generic /boot/vmlinuz-3.2.0-64-generic
Errors were encountered while processing:
 /var/cache/apt/archives/linux-image-3.2.0-64-generic_3.2.0-64.97_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Ok, let's remove old kernels:

```
[FONT=Ubuntu Mono]sudo apt-get remove --purge $(dpkg -l 'linux-*' | sed '/^ii/!d;/'"$(uname -r | sed "s/\(.*\)-\([^0-9]\+\)/\1/")"'/d;s/^[^ ]* [^ ]* \([^ ]*\).*/\1/;/[0-9]/!d')[/FONT]
```

Sill complains about unmet dependencies.  I even tried to install gpart to resize the partition, but it still complains about unmet dependencies.

I feel stuck.  Any ideas?

---

### Post by stalkingwolf on 2014-06-16
try using the gparted live disk.

---

### Post by Bucky Ball on 2014-06-16
Try these three commands, one at a time, and post back exactly what errors you encounter:
```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```

---

### Post by Jason_Canup on 2014-06-16
Here ya go:

```

Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 linux-generic : Depends: linux-headers-generic (= 3.2.0.61.72) but 3.2.0.64.76 is installed
E: Unmet dependencies. Try using -f.
```

---

### Post by Bucky Ball on 2014-06-16
Give it a try, then:

```
sudo apt-get -f install
```

---

### Post by Jason_Canup on 2014-06-16
```
Reading package lists... DoneBuilding dependency tree
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 62 not upgraded.
3 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up linux-image-3.2.0-61-generic (3.2.0-61.92) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
The link /initrd.img is a dangling linkto /boot/initrd.img-3.2.0-63-generic
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.2.0-61-generic /boot/vmlinuz-3.2.0-61-generic
run-parts: executing /etc/kernel/postinst.d/dkms 3.2.0-61-generic /boot/vmlinuz-3.2.0-61-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.2.0-61-generic /boot/vmlinuz-3.2.0-61-generic
update-initramfs: Generating /boot/initrd.img-3.2.0-61-generic


gzip: stdout: No space left on device
E: mkinitramfs failure cpio 141 gzip 1
update-initramfs: failed for /boot/initrd.img-3.2.0-61-generic with 1.
run-parts: /etc/kernel/postinst.d/initramfs-tools exited with return code 1
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.2.0-61-generic.postinst line 1010.
dpkg: error processing linux-image-3.2.0-61-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up linux-image-3.2.0-63-generic (3.2.0-63.95) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
The link /initrd.img is a dangling linkto /boot/initrd.img-3.2.0-61-generic
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.2.0-63-generic /boot/vmlinuz-3.2.0-63-generic
run-parts: executing /etc/kernel/postinst.d/dkms 3.2.0-63-generic /boot/vmlinuz-3.2.0-63-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.2.0-63-generic /boot/vmlinuz-3.2.0-63-generic
update-initramfs: Generating /boot/initrd.img-3.2.0-63-generic


gzip: stdout: No space left on device
E: mkinitramfs failure cpio 141 gzip 1
update-initramfs: failed for /boot/initrd.img-3.2.0-63-generic with 1.
run-parts: /etc/kernel/postinst.d/initramfs-tools exited with return code 1
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.2.0-63-generic.postinst line 1010.
dpkg: error processing linux-image-3.2.0-63-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-3.2.0-61-generic; however:
  Package linux-image-3.2.0-61-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          Errors were encountered while processing:
 linux-image-3.2.0-61-generic
 linux-image-3.2.0-63-generic
 linux-image-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by Bashing-om on 2014-06-16
Jason_Canup; et all .. hey, hey ;

This one might get interesting !
> 
The link /initrd.img is a dangling linkto /boot/initrd.img-3.2.0-61-generic


So let's see what that situation is; Post back the outputs of terminal commands:
```

ls -la /
la -la /boot

```
and confirm we are dealing with release 12.04.X
```

lsb_release -a
uname -a

```

In respect to:
> 
gzip: stdout: No space left on device

What does the package manager think about the installed kernels ?
```

df -h
df -i
dpkg -l | grep "linux-*"

```

See what it is going to take to get us some operating head room in the /boot directory and then see about repairing that initrd.img symbolic link.
Recon the package manager will take care of the broken link once the old kernels are removed, or will we have to manually intervene and declare that link ?

[INDENT][INDENT]inquiring minds want to know
[/INDENT][/INDENT]

---

### Post by Jason_Canup on 2014-06-17
So let's see what that situation is; Post back the outputs of terminal commands:


```
$ ls -la 
/total 129
drwxr-xr-x  27 root root  4096 Jun 16 15:35 .
drwxr-xr-x  27 root root  4096 Jun 16 15:35 ..
drwxr-xr-x   2 root root 12288 Apr 10 13:05 bin
drwxr-xr-x   4 root root  1024 Jun 16 15:35 boot
drwxr-xr-x   2 root root  4096 Dec 17  2012 cdrom
drwxr-xr-x  15 root root  4180 Jun 17 00:10 dev
drwxr-xr-x 155 root root 12288 Jun 16 15:40 etc
drwxr-xr-x   4 root root  4096 May 16 10:40 home
drwxr-xr-x  26 root root  4096 Apr 14 12:46 lib
drwxr-xr-x   2 root root  4096 Apr 14 12:45 lib32
drwxr-xr-x   2 root root  4096 Apr 10 12:57 lib64
drwx------   2 root root 16384 Apr 10 12:42 lost+found
drwxr-xr-x   3 root root  4096 Apr 11 16:25 media
drwxr-xr-x   2 root root  4096 Dec 18  2012 mnt
drwxr-xr-x   6 root root  4096 Apr 10 16:22 nsm
drwxr-xr-x  14 root root  4096 Apr 22 11:57 opt
dr-xr-xr-x 273 root root     0 Jun 16 14:58 proc
-rw-r--r--   1 root root  1824 Jun 16 10:31 report.xml
drwx------  10 root root  4096 Jun 16 13:39 root
drwxr-xr-x  29 root root  1040 Jun 17 08:30 run
drwxr-xr-x   2 root root 12288 Jun 16 14:25 sbin
drwxr-xr-x   2 root root  4096 Mar  5  2012 selinux
drwxr-xr-x   2 root root  4096 Apr 25  2012 srv
drwxr-xr-x  13 root root     0 Jun 16 14:58 sys
drwxrwxrwt  12 root root  4096 Jun 17 08:30 tmp
drwxr-xr-x  12 root root  4096 Apr 14 12:45 usr
drwxr-xr-x  15 root root  4096 Jun 16 14:58 var
lrwxrwxrwx   1 root root    29 Jun 16 15:33 vmlinuz -> boot/vmlinuz-3.2.0-63-generic
lrwxrwxrwx   1 root root    29 Jun 16 15:32 vmlinuz.old -> boot/vmlinuz-3.2.0-61-generic
drwxr-xr-x   2 root root  4096 Apr 10 13:10 www

$ la -la /boot
total 77096
drwxr-xr-x  4 root root     1024 Jun 16 15:35 .
drwxr-xr-x 27 root root     4096 Jun 16 15:35 ..
-rw-r--r--  1 root root   795365 Jul 26  2013 abi-3.2.0-52-generic
-rw-r--r--  1 root root   795743 Feb 18 23:33 abi-3.2.0-60-generic
-rw-r--r--  1 root root   795743 Mar 31 20:13 abi-3.2.0-61-generic
-rw-r--r--  1 root root   795911 May 15 19:44 abi-3.2.0-63-generic
-rw-r--r--  1 root root   140629 Jul 26  2013 config-3.2.0-52-generic
-rw-r--r--  1 root root   140612 Feb 18 23:33 config-3.2.0-60-generic
-rw-r--r--  1 root root   140612 Mar 31 20:13 config-3.2.0-61-generic
-rw-r--r--  1 root root   140640 May 15 19:44 config-3.2.0-63-generic
drwxr-xr-x  3 root root     7168 Apr 10 13:09 grub
-rw-r--r--  1 root root 21632966 Apr 10 12:57 initrd.img-3.2.0-52-generic
-rw-r--r--  1 root root 21669113 Apr 10 13:10 initrd.img-3.2.0-60-generic
drwx------  2 root root    12288 Apr 10 12:42 lost+found
-rw-r--r--  1 root root   176764 Nov 27  2011 memtest86+.bin
-rw-r--r--  1 root root   178944 Nov 27  2011 memtest86+_multiboot.bin
-rw-------  1 root root  2893555 Jul 26  2013 System.map-3.2.0-52-generic
-rw-------  1 root root  2895229 Feb 18 23:33 System.map-3.2.0-60-generic
-rw-------  1 root root  2895229 Mar 31 20:13 System.map-3.2.0-61-generic
-rw-------  1 root root  2896164 May 15 19:44 System.map-3.2.0-63-generic
-rw-r--r--  1 root root  4978224 Sep  4  2013 vmlinuz-3.2.0-52-generic
-rw-------  1 root root  4981616 Feb 18 23:33 vmlinuz-3.2.0-60-generic
-rw-------  1 root root  4981616 Mar 31 20:13 vmlinuz-3.2.0-61-generic
-rw-------  1 root root  4985488 May 15 19:44 vmlinuz-3.2.0-63-generic
```

In respect to:

What does the package manager think about the installed kernels ?


```
$ df -h
df: `/var/lib/lightdm/.gvfs': Permission denied
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda4       3.6T  2.7T  711G  80% /
udev            7.8G  4.0K  7.8G   1% /dev
tmpfs           1.6G  936K  1.6G   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            7.8G  176K  7.8G   1% /run/shm
/dev/sda2        92M   85M  2.6M  98% /boot

$ df -i
df: `/var/lib/lightdm/.gvfs': Permission denied
Filesystem        Inodes  IUsed     IFree IUse% Mounted on
/dev/sda4      243204096 331066 242873030    1% /
udev             2035400    511   2034889    1% /dev
tmpfs            2038507    480   2038027    1% /run
none             2038507      2   2038505    1% /run/lock
none             2038507     36   2038471    1% /run/shm
/dev/sda2          24384    243     24141    1% /boot

$ dpkg -l | grep "linux-*"
ii  libselinux1                                                2.1.0-4.1ubuntu1                          SELinux runtime shared libraries
ii  libselinux1:i386                                           2.1.0-4.1ubuntu1                          SELinux runtime shared libraries
ii  libv4l-0                                                   0.8.6-1ubuntu2                            Collection of video4linux support libraries
ii  libv4l-0:i386                                              0.8.6-1ubuntu2                            Collection of video4linux support libraries
ii  libv4lconvert0                                             0.8.6-1ubuntu2                            Video4linux frame format conversion library
ii  libv4lconvert0:i386                                        0.8.6-1ubuntu2                            Video4linux frame format conversion library
ii  linux-firmware                                             1.79.15                                   Firmware for Linux kernel drivers
ii  linux-headers-3.2.0-60                                     3.2.0-60.91                               Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-60-generic                             3.2.0-60.91                               Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-3.2.0-61                                     3.2.0-61.93                               Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-61-generic                             3.2.0-61.93                               Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-3.2.0-63                                     3.2.0-63.95                               Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-63-generic                             3.2.0-63.95                               Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-3.2.0-64                                     3.2.0-64.97                               Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-64-generic                             3.2.0-64.97                               Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-generic                                      3.2.0.64.76                               Generic Linux kernel headers
ii  linux-image-3.2.0-52-generic                               3.2.0-52.78                               Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-60-generic                               3.2.0-60.91                               Linux kernel image for version 3.2.0 on 64 bit x86 SMP
iF  linux-image-3.2.0-61-generic                               3.2.0-61.92                               Linux kernel image for version 3.2.0 on 64 bit x86 SMP
iF  linux-image-3.2.0-63-generic                               3.2.0-63.95                               Linux kernel image for version 3.2.0 on 64 bit x86 SMP
iU  linux-image-generic                                        3.2.0.61.72                               Generic Linux kernel image
ii  linux-libc-dev                                             3.2.0-63.95                               Linux Kernel Headers for development
ii  linux-sound-base                                           1.0.25+dfsg-0ubuntu1.1                    base package for ALSA and OSS sound systems
ii  pptp-linux                                                 1.7.2-6                                   Point-to-Point Tunneling Protocol (PPTP) Client
ii  securityonion-libsys-info-driver-linux-perl                0.7901-1ubuntu1securityonion9             main module in the Sys::Info Linux driver collection.
ii  syslinux                                                   2:4.05+dfsg-2                             collection of boot loaders
ii  syslinux-common                                            2:4.05+dfsg-2                             collection of boot loaders (common files)
ii  syslinux-legacy                                            2:3.63+dfsg-2ubuntu5                      Bootloader for Linux/i386 using MS-DOS floppies
ii  util-linux                                                 2.20.1-1ubuntu3                           Miscellaneous system utilities
```
[INDENT][INDENT]
[/INDENT]
[/INDENT]
Thanks for any help you can give!  This one has been pretty frustrating and I don't want to reload....

---

### Post by Jason_Canup on 2014-06-17
Forgot this one:

```
$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 12.04.4 LTS
Release:        12.04
Codename:       precise

$ uname -a
Linux SCIENTES 3.2.0-60-generic #91-Ubuntu SMP Wed Feb 19 03:54:44 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux
```

---

### Post by Bucky Ball on 2014-06-17
Wondering if this might work. I use Synaptic Package Manager to clear out old kernels so not sure how you'd go about it otherwise. Possibly Software Centre?

Anyhow, in either of those, do a search for 'linux image'. You should get a heap. Have a look at the installed ones (easy in Synaptics). You are using 3.2.0-60-generic so you might want to keep that and the one below that, 3.2.0-59-generic I don't doubt, and delete the rest. This *should* clear out a heap of room on your boot partition.

Then you can update/upgrade/dist-upgrade to get to the latest kernel, and not before time, as the latest is 3.2.0-64-generic so it's been awhile since you could update/upgrade by the looks ... ;)

---

### Post by Jason_Canup on 2014-06-17
Hey Bucky,

According to Synaptic, I currently have 3.2.2.60, 3.2.0.61, 3.2.0.63 and 3.2.0.64 installed.  No earlier packages detected.  I'm a little confused as to what to do based on that.

---

### Post by Bucky Ball on 2014-06-17
Ah ha. Open a terminal any way you can and:

```
sudo update-grub
```

Reboot and choose the -64 kernel ...

That command doesn't need you to be online so hopefully the new kernel will meet the dependencies. At least, that's the plan. ;)

---

### Post by Bashing-om on 2014-06-17
Jason_Canup; Bucky Ball -> Hey !


Yes agreed we need to get rid of all those old kernels, But;
This:
> 
$ ls -la 
/total 129
drwxr-xr-x  27 root root  4096 Jun 16 15:35 .
drwxr-xr-x  27 root root  4096 Jun 16 15:35 ..
drwxr-xr-x   2 root root 12288 Apr 10 13:05 bin
drwxr-xr-x   4 root root  1024 Jun 16 15:35 boot
drwxr-xr-x   2 root root  4096 Dec 17  2012 cdrom
drwxr-xr-x  15 root root  4180 Jun 17 00:10 dev
drwxr-xr-x 155 root root 12288 Jun 16 15:40 etc
drwxr-xr-x   4 root root  4096 May 16 10:40 home
drwxr-xr-x  26 root root  4096 Apr 14 12:46 lib
drwxr-xr-x   2 root root  4096 Apr 14 12:45 lib32
drwxr-xr-x   2 root root  4096 Apr 10 12:57 lib64
drwx------   2 root root 16384 Apr 10 12:42 lost+found
drwxr-xr-x   3 root root  4096 Apr 11 16:25 media
drwxr-xr-x   2 root root  4096 Dec 18  2012 mnt
drwxr-xr-x   6 root root  4096 Apr 10 16:22 nsm
drwxr-xr-x  14 root root  4096 Apr 22 11:57 opt
dr-xr-xr-x 273 root root     0 Jun 16 14:58 proc
-rw-r--r--   1 root root  1824 Jun 16 10:31 report.xml
drwx------  10 root root  4096 Jun 16 13:39 root
drwxr-xr-x  29 root root  1040 Jun 17 08:30 run
drwxr-xr-x   2 root root 12288 Jun 16 14:25 sbin
drwxr-xr-x   2 root root  4096 Mar  5  2012 selinux
drwxr-xr-x   2 root root  4096 Apr 25  2012 srv
drwxr-xr-x  13 root root     0 Jun 16 14:58 sys
drwxrwxrwt  12 root root  4096 Jun 17 08:30 tmp
drwxr-xr-x  12 root root  4096 Apr 14 12:45 usr
drwxr-xr-x  15 root root  4096 Jun 16 14:58 var
lrwxrwxrwx   1 root root    29 Jun 16 15:33 vmlinuz -> boot/vmlinuz-3.2.0-63-generic
lrwxrwxrwx   1 root root    29 Jun 16 15:32 vmlinuz.old -> boot/vmlinuz-3.2.0-61-generic
drwxr-xr-x   2 root root  4096 Apr 10 13:10 www

Bothers me a bunch as there is no initrd.img link to any image file: as in mine:
> 
sysop@1310mini:~$ ls -la /
<snip>
drwxr-xr-x   4 root root  4096 May 19  2013 home
lrwxrwxrwx   1 root root    33 Jun 13 00:07 initrd.img -> boot/initrd.img-3.11.0-23-generic
lrwxrwxrwx   1 root root    34 Jun 13 00:07 initrd.img.old -> /boot/initrd.img-3.11.0-23-generic
drwxr-xr-x  21 root root  4096 Dec 22 10:23 lib
<snip>

What do yall think about running 'update-initramfs' with the -u and -k arguments, and maybe rebuild that link ???

Keep in mind that the /boot partition is tiny:
```

/dev/sda2        92M   85M  2.6M  98% /boot

``` thus will require that you, Jason, keep a close eye on it to preclude this happening again, it will fill up with only 2 additional kernels installed. - Once this situation is resolved.

I am 
[INDENT][INDENT]open to a learning experience
[/INDENT][/INDENT]

---

### Post by SaturnusDJ on 2014-07-20
I fixed a very similar problem this way:
- Download the latest version of the problem giving package(s) as deb. In your case linux-headers-generic and libgtkmm-2.4-1c2a.
- Force this package(s) to be installed with this command: ```
dpkg -i --force-all the-deb-file.deb
```

Maybe you need to do the same for dependencies of these packages.

---

