---
title: "Re-compiling Gutsy"
date: 2008-01-10
forum: General Help
---

### Post by Mithrilhall on 2008-01-10
What is the easiest way to recompile the kernel in Gutsy? I have to apply some patches and recompile the kernel.

---

### Post by Craigus on 2008-01-10
[http://ubuntuforums.org/showthread.php?t=311158]("http://ubuntuforums.org/showthread.php?t=311158")

[https://help.ubuntu.com/community/Kernel/Compile]("https://help.ubuntu.com/community/Kernel/Compile")

[http://ubuntuforums.org/showthread.php?t=56835]("http://ubuntuforums.org/showthread.php?t=56835")

For compiling the latest vanilla kernel:

[http://ubuntuforums.org/showthread.php?t=618563]("http://ubuntuforums.org/showthread.php?t=618563")

---

### Post by Mithrilhall on 2008-01-10
Thanks I'll give these a shot.

I've followed at least 1 of these and it didn't work but a few of the others look like they might do the trick.

---

### Post by Mithrilhall on 2008-01-11
None of the links provided anything that worked for me. The problem I'm having is before I install the new kernel and reboot I have two network cards (eth0 and eth1). Once I install the new kernel and boot that I only have one network card showing (eth0). :confused:

This is what I'm getting when I try to install the new kernel:

```

root@ms:/usr/src# dpkg -i linux-image-2.6.22.9-mastershaper0.1_2.6.22.9-mastershaper0.1-10.00.Custom_i386.deb
(Reading database ... 106560 files and directories currently installed.)
Preparing to replace linux-image-2.6.22.9-mastershaper0.1 2.6.22.9-mastershaper0.1-10.00.Custom (using linux-image-2.6.22.9-mastershaper0.1_2.6.22.9-mastershaper0.1-10.00.Custom_i386.deb) ...
Done.
Unpacking replacement linux-image-2.6.22.9-mastershaper0.1 ...
Running postrm hook script /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.22.9-mastershaper0.1
Found kernel: /boot/vmlinuz-2.6.22-14-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

Setting up linux-image-2.6.22.9-mastershaper0.1 (2.6.22.9-mastershaper0.1-10.00.Custom) ...
Running depmod.
Finding valid ramdisk creators.
Using mkinitramfs-kpkg to build the ramdisk.
Other valid candidates: mkinitramfs-kpkg mkinitrd.yaird
find: /lib/firmware/2.6.22.9-mastershaper0.1: No such file or directory
find: /lib/firmware/2.6.22.9-mastershaper0.1: No such file or directory
find: /lib/firmware/2.6.22.9-mastershaper0.1: No such file or directory
find: /lib/firmware/2.6.22.9-mastershaper0.1: No such file or directory
find: /lib/firmware/2.6.22.9-mastershaper0.1: No such file or directory
find: /lib/firmware/2.6.22.9-mastershaper0.1: No such file or directory
Not updating initrd symbolic links since we are being updated/reinstalled
(2.6.22.9-mastershaper0.1-10.00.Custom was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled
(2.6.22.9-mastershaper0.1-10.00.Custom was configured last, according to dpkg)
Running postinst hook script update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.22.9-mastershaper0.1
Found kernel: /boot/vmlinuz-2.6.22-14-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done


root@ms:/usr/src#

```

---

### Post by Mithrilhall on 2008-01-11
I'm going to give Sidux a try and I'll see if that goes better.

---

### Post by Craigus on 2008-01-12
That looks like a normal kernel install to me.

The lines:

```
find: /lib/firmware/2.6.22.9-mastershaper0.1: No such file or directory
find: /lib/firmware/2.6.22.9-mastershaper0.1: No such file or directory
find: /lib/firmware/2.6.22.9-mastershaper0.1: No such file or directory
find: /lib/firmware/2.6.22.9-mastershaper0.1: No such file or directory
find: /lib/firmware/2.6.22.9-mastershaper0.1: No such file or directory
find: /lib/firmware/2.6.22.9-mastershaper0.1: No such file or directory
```

are normal and do not indicate that anything bad has happened.

The nic problem may be occuring because your new kernel does not have support for one of the devices. What are they ?

---

### Post by Washer on 2008-01-12
Hmm does kernelcheck hydra allow a custom patch?

---

### Post by Mithrilhall on 2008-01-15
> 
That looks like a normal kernel install to me.


That's odd. I never get this type of message with Debian.

> 
00:19.0 Ethernet controller: Intel Corporation 82566DM-2 Gigabit Network Connection (rev 02)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8169 Gigabit Ethernet (rev 10)


---

### Post by Craigus on 2008-01-15
Which one doesn't work with the new kernel ?

---

### Post by Mithrilhall on 2008-01-16
I believe it's the Intel.

---

### Post by DagMan on 2008-01-16
Try booting into your normal kernel and then doing this
sudo ln -s /lib/firmware/`uname -r` /lib/firmware/2.6.22.9-mastershaper0.1

There may be a binary file as well that needs to be symlinked or copied with a new name for the interface to work, and maybe still it's not enough but the above is necessary if it's going to work at all.

---

### Post by jerrykenny on 2008-01-16
Try this

[http://ubuntuforums.org/showthread.php?t=668938&highlight=firmware](http://ubuntuforums.org/showthread.php?t=668938&highlight=firmware)

---

