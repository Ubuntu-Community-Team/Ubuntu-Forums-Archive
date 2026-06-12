---
title: "Xen w/ Raid boot issue"
date: 2007-07-04
forum: General Help
---

### Post by floydwilde on 2007-07-04
I have a setup, 3 250 GB sata hd's in a RAID array, running latest feisty:

$ uname -a
Linux satori 2.6.20-16-generic #2 SMP Thu Jun 7 20:19:32 UTC 2007 i686 GNU/Linux

I setup a /boot and / 'root' partition with RAID-1, and then a largish RAID-0 partition mounted on /var

After doing just a regular feisty install using the alternate install disk, I had some issues booting.  It would get so far and then stop and hang for while, and eventually dump me into an unusable busy box shell.  

I found some solutions to this, one was to append break=mount to the kernel boot command in grub.  Then when I got into the busy box shell, I just had to press ctrl-d, and it would magically boot.  The other final solution I found was to edit /etc/default/mdadm and set it to only mount the root partition, and bring the other array up later. 

INITRDSTART='/dev/md1'

Now everything works fine, but I want to use xen, so I installed the ubuntu-xen-desktop package and have a similar boot problem.  Only the break=mount command doesn't help me get past the busy box shell, and when I try to update the initrd image, I get this error 

john@satori:/boot$ sudo update-initramfs -k 2.6.19-4-generic -u
update-initramfs: Generating /boot/initrd.img-2.6.19-4-generic
find: /lib/firmware/2.6.19-4-generic: No such file or directory
find: /lib/firmware/2.6.19-4-generic: No such file or directory
find: /lib/firmware/2.6.19-4-generic: No such file or directory
find: /lib/firmware/2.6.19-4-generic: No such file or directory
find: /lib/firmware/2.6.19-4-generic: No such file or directory
find: /lib/firmware/2.6.19-4-generic: No such file or directory
john@satori:/boot$ 

Anyone know what this means?  And how to get xen booting with RAID?  I installed xen on a non-raid setup, and it works fine.

---

