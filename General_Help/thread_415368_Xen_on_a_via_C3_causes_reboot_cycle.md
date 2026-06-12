---
title: "Xen on a via C3 causes reboot cycle"
date: 2007-04-20
forum: General Help
---

### Post by azelter on 2007-04-20
I'm currently trying to get Xen working on my server by following the instructions on:
[https://help.ubuntu.com/community/XenVirtualMachine/XenOnUbuntuFeisty](https://help.ubuntu.com/community/XenVirtualMachine/XenOnUbuntuFeisty)

After installing the ubuntu-xen-desktop package I have an entry in my grub file like this:
title           Xen 3.0-i386 / Ubuntu, kernel 2.6.19-4-generic
root            (hd0,0)
kernel          /boot/xen-3.0-i386.gz
module          /boot/vmlinuz-2.6.19-4-generic root=UUID=cfef64ea-31c1-4f82-b739-03605102a34c ro console=tty0
module          /boot/initrd.img-2.6.19-4-generic
savedefault

When I reboot, however, the computer goes through grub, trys to boot the ext2 initramfs and just beeps and reboots itself without getting any further. I'm not sure what could be happening. My processor is a via C3 (specs below) and this is the output I get when dpkg is setting up the xen kernel:
Setting up xen-image-2.6.19-4-generic (2.6.19-2ubuntu7) ...
update-initramfs: Generating /boot/initrd.img-2.6.19-4-generic
find: /lib/firmware/2.6.19-4-generic: No such file or directory
find: /lib/firmware/2.6.19-4-generic: No such file or directory
find: /lib/firmware/2.6.19-4-generic: No such file or directory
find: /lib/firmware/2.6.19-4-generic: No such file or directory
find: /lib/firmware/2.6.19-4-generic: No such file or directory
find: /lib/firmware/2.6.19-4-generic: No such file or directory
W: mdadm: unchecked configuration file: /etc/mdadm/mdadm.conf
W: mdadm: please read /usr/share/doc/mdadm/README.upgrading-2.5.3.gz .
Searching for GRUB installation directory ... found: /boot/grub
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found Xen hypervisor 3.0-i386,  kernel: /boot/vmlinuz-2.6.19-4-generic
Found kernel: /boot/vmlinuz-2.6.20-15-386
Found kernel: /boot/vmlinuz-2.6.19-4-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

Any pointers as to what I can do to fix this would be very much appreciated!


processor       : 0
vendor_id       : CentaurHauls
cpu family      : 6
model           : 7
model name      : VIA Samuel 2
stepping        : 3
cpu MHz         : 796.161
cache size      : 64 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 1
wp              : yes
flags           : fpu de tsc msr cx8 mtrr pge mmx 3dnow
bogomips        : 1594.36
clflush size    : 32

---

### Post by azelter on 2007-04-20
OK, answering my own post but ...
It seems other people have had this problem (see [http://lists.xensource.com/archives/html/xen-users/2006-02/msg00901.html)](http://lists.xensource.com/archives/html/xen-users/2006-02/msg00901.html)).
After more searching it seems that some of the via processors have issues due to 4kb pages and no cmov instruction and therefore require the patch Adam Sulmicki put together for Xen 2.0.0 and 2.0.1 ([http://lists.xensource.com/archives/html/xen-users/2005-10/msg00050.html)](http://lists.xensource.com/archives/html/xen-users/2005-10/msg00050.html)). However, this patch will not work on newer versions of Xen ([http://lists.xensource.com/archives/html/xen-users/2005-10/msg00036.html)](http://lists.xensource.com/archives/html/xen-users/2005-10/msg00036.html)).

So as both vmware and kvm also do not function with this processor my choices for virtulization are rapidly diminishing. Shame as the processor is perfect for a small low power usage server...

---

