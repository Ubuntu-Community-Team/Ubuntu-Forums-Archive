---
title: "Problem with mounting NTFS partition (unrecognized option '--no-canonicalize')"
date: 2016-03-31
forum: General Help
---

### Post by rchr on 2016-03-31
Helo guys,

I`m on Ubuntu 14.04.4 (with MATE 1.8) and I have a weird issue with mounting NTFS partition (on USB pendrive).
I`m able to format it into NTFS using gnome-disk-utility and I believe I have all required NTFS packages installed.
However it won`t mount... always giving me such message:

[IMG]http://i.imgur.com/fRwCuHe.png[/IMG]

I`ve been searching the web for solution, but can`t find anything useful...
Tried mounting manually via Bash or even some special tool (I believe "usbmount"), but it does not work either.

I remember that couple years ago, when I had previous, older installation of Ubuntu, NTFS was working fine... but now it's this.
I`ve noticed this issue first maybe over a year ago, but couldn`t fix it so gave up. However now I need it much more for moving large files between Windows-Linux.

Please help me find a solution. I have no idea what more can I do.

Best Regards

---

### Post by yancek on 2016-03-31
Post the actual complete command you use to try to mount.

---

### Post by rchr on 2016-03-31
All I could figure is to simplify the original Caja command...

> root@chr-dev:/home/chr# mount -t "ntfs" "/dev/sdd1" "/media/img"
/bin/mount: unrecognized option '--no-canonicalize'
Usage: mount -V                 : print version
       mount -h                 : print this help
       mount                    : list mounted filesystems
       mount -l                 : idem, including volume labels
So far the informational part. Next the mounting.
The command is `mount [-t fstype] something somewhere'.
Details found in /etc/fstab may be omitted.
       mount -a [-t|-O] ...     : mount all stuff from /etc/fstab
       mount device             : mount device at the known place
       mount directory          : mount known device here
       mount -t type dev dir    : ordinary mount command
Note that one does not really mount a device, one mounts
a filesystem (of the given type) found on the device.
One can also mount an already visible directory tree elsewhere:
       mount --bind olddir newdir
or move a subtree:
       mount --move olddir newdir
One can change the type of mount containing the directory dir:
       mount --make-shared dir
       mount --make-slave dir
       mount --make-private dir
       mount --make-unbindable dir
One can change the type of all the mounts in a mount subtree
containing the directory dir:
       mount --make-rshared dir
       mount --make-rslave dir
       mount --make-rprivate dir
       mount --make-runbindable dir
A device can be given by name, say /dev/hda1 or /dev/cdrom,
or by label, using  -L label  or by uuid, using  -U uuid .
Other options: [-nfFrsvw] [-o options] [-p passwdfd].
For many more details, say  man 8 mount .

PS.
The issue always seems to be this '--no-canonicalize' option thing. I`ve searched it, read about it, but still have no clue what to do to skip/fix it.
Something seems to be forcing this option, but my mount don`t supports it, even though some MAN pages about mount lists it, like here:
[http://manpages.ubuntu.com/manpages/precise/man8/mount.8.html](http://manpages.ubuntu.com/manpages/precise/man8/mount.8.html)

PS2.
Oh, and here`s my mount version:
> chr@chr-dev:~$ mount --version
mount from util-linux-ng 2.16.2 (with libblkid and selinux support)

PS3.
And it`s even weirder because Synaptic and APT shows different version: 2.20.1-5.1ubuntu20.7
> root@chr-dev:/home/chr# apt-cache show mount
Package: mount
Essential: yes
Priority: required
Section: admin
Installed-Size: 421
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: LaMont Jones <lamont@debian.org>
Architecture: amd64
Source: util-linux
Version: 2.20.1-5.1ubuntu20.7
Pre-Depends: libblkid1 (>= 2.20.1), libc6 (>= 2.14), libmount1 (>= 2.20.1), libselinux1 (>= 2.0.15)
Suggests: nfs-common (>= 1:1.1.0-13)
Filename: pool/main/u/util-linux/mount_2.20.1-5.1ubuntu20.7_amd64.deb
Size: 114386
MD5sum: 45697f0d8a43026d057a54d15b412b82
SHA1: f9c3ec51b8b5f4e214bd05d8cf6ffcd8e3d77239
SHA256: dff9f2bb4dd9ca80e2328f325537451c4ae0db7c68284940b2d58e18a26ebd1c
Description-pl: Narz&#281;dzia do montowania i manipulowania systemami plików
 Ten pakiet udost&#281;pnia polecenia mount(8), umount(8), swapon(8),
 swapoff(8), oraz losetup(8).
Description-md5: 46eb8e09a600d5eb98b6b40428349102
Multi-Arch: foreign
Homepage: [http://userweb.kernel.org/~kzak/util-linux/](http://userweb.kernel.org/~kzak/util-linux/)
Bugs: [https://bugs.launchpad.net/ubuntu/+filebug](https://bugs.launchpad.net/ubuntu/+filebug)
Origin: Ubuntu
Supported: 5y
Task: minimal

Package: mount
Essential: yes
Priority: required
Section: admin
Installed-Size: 420
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: LaMont Jones <lamont@debian.org>
Architecture: amd64
Source: util-linux
Version: 2.20.1-5.1ubuntu20
Pre-Depends: libblkid1 (>= 2.20.1), libc6 (>= 2.14), libmount1 (>= 2.20.1), libselinux1 (>= 2.0.15)
Suggests: nfs-common (>= 1:1.1.0-13)
Filename: pool/main/u/util-linux/mount_2.20.1-5.1ubuntu20_amd64.deb
Size: 114528
MD5sum: b07fb01262182535251d1db1dbd2c8b8
SHA1: 02bb91c836496b26890241252623ad325c689db1
SHA256: b55d1f6dba47e27fad27daea548ec868688452ad2d573faf8bb45acc488b3e89
Description-pl: Narz&#281;dzia do montowania i manipulowania systemami plików
 Ten pakiet udost&#281;pnia polecenia mount(8), umount(8), swapon(8),
 swapoff(8), oraz losetup(8).
Description-md5: 46eb8e09a600d5eb98b6b40428349102
Multi-Arch: foreign
Homepage: [http://userweb.kernel.org/~kzak/util-linux/](http://userweb.kernel.org/~kzak/util-linux/)
Bugs: [https://bugs.launchpad.net/ubuntu/+filebug](https://bugs.launchpad.net/ubuntu/+filebug)
Origin: Ubuntu
Supported: 5y
Task: minimal

---

### Post by rchr on 2016-03-31
Oh xD Just rememebered that I had same issue with mounting TrueCrypt drive long time ago:
[URL="https://bugs.launchpad.net/ubuntu/+source/loop-aes-utils/+bug/731228"]
[https://bugs.launchpad.net/ubuntu/+source/loop-aes-utils/+bug/727220](https://bugs.launchpad.net/ubuntu/+source/loop-aes-utils/+bug/727220)
[/URL]
It`s a loop-aes-utils bug known for 5 years and they even claim it`s been fixed in loop-aes-utils-2.16.2-1ubuntu0.1 but I`ve been using exactly this version...
However updating to 2.16.2-3 fixed the issue somehow! So I`m so happy xD

---

### Post by ajgreeny on 2016-03-31
Can we check that you have not attached this usb drive to a Windows machine and simply unplugged it without removing it safely.

Also have a look at [http://ubuntuforums.org/showthread.php?t=2133606](http://ubuntuforums.org/showthread.php?t=2133606) where the thread talks about the same error showing.

---

### Post by rchr on 2016-03-31
Nah, haven`t connected this to Windows even once. However I`ve found a fix and updated my previous post with how ;)
Thanks anyway!

---

### Post by rchr on 2016-03-31
Just one more thing I`ve been wondering for a long time but totally forgot about...
Why is it that official Ubuntu repo doesn`t have/maintain loop-aes-utils anymore ?
It`s so useful tool...
I need to keep my own, old .deb package...

---

