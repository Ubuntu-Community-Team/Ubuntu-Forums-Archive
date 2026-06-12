---
title: "[SOLVED] Grub Won't Boot Windows"
date: 2008-06-09
forum: General Help
---

### Post by gus_zernial on 2008-06-09
I have a Kubuntu 8.04 system with three disks - the first two are Linux in software RAID and the third is Windows XP. My fdisk -l is below. When I do root (hd <TAB> in grub it gives me choices hd0, hd1, hd2; for hd0 and
hd1 it shows the Linux partitions; so grub identifies hd2 as the Windows
disk. In menu.lst my Windows entry is:

title           Windows XP
rootnoverify    (hd2,0)
makeactive
chainloader     +1

Linux boots fine, but Grub won't boot Windows. When it tries to boot
Windows it displays "Starting ...." and then stalls. If I re-prioritize
the disks in the BIOS, the Windows disk boots fine, so I think the Windows
install itself is OK. Appreciate ideas how to diagnose and modify Grub
and menu.lst to get Windows to boot from Grub.

-------------
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

title		Ubuntu 8.04, kernel 2.6.24-18-generic
root		(hd0,0)
kernel		/vmlinuz-2.6.24-18-generic root=/dev/md1 ro quiet splash
initrd		/initrd.img-2.6.24-18-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-18-generic (recovery mode)
root		(hd0,0)
kernel		/vmlinuz-2.6.24-18-generic root=/dev/md1 ro single
initrd		/initrd.img-2.6.24-18-generic

title           Windows XP
rootnoverify    (hd2,0)
makeactive
chainloader     +1

title		Ubuntu 8.04, kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/vmlinuz-2.6.22-14-generic root=/dev/md1 ro quiet splash
initrd		/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 8.04, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,0)
kernel		/vmlinuz-2.6.22-14-generic root=/dev/md1 ro single
initrd		/initrd.img-2.6.22-14-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,0)
kernel		/memtest86+.bin
quiet

---

### Post by plucky on 2008-06-09
No guarantees,but this sounds like windows doesn't like being on HD2 instead of HD0.I can't verify this personally but see this link [http://users.bigpond.net.au/hermanzone/p15.htm#Chainloading_Windows_using_map_commands](http://users.bigpond.net.au/hermanzone/p15.htm#Chainloading_Windows_using_map_commands) for how to trick windows into thinking it is on HD0.


You probably have to use ```
map (hd0) (hd2)
map (hd2) (hd0)
``` instead of what is shown in the example at the link.


Good luck

---

### Post by gus_zernial on 2008-06-09
That was it - thanks Plucky!

---

