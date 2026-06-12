---
title: "i need some advanced GRUB help! please! :("
date: 2008-05-05
forum: General Help
---

### Post by ijason on 2008-05-05
greetings. 

i was finishing the last steps of doing a dual boot with windows XP and ubunt7.10 when the GRUB hit the fan. the back-story is that i used gparted to create two ntfs partitions, one ext2 partition, and one swap partition on my laptop's HD. i installed windows on the smaller ntfs partition and ubuntu7.10 on the ext2 partition - leaving the bigger ntfs partition for shared files between the two, and obviously the swap for swap.

windows installed fine. then ubuntu installed fine. but on reboot, i got a grub error 17.

i tried the usual first steps of booting off a cd (a Partimage system rescue cd) and getting a command-line to do the following :
> /root % grub
/ GRUB > find /boot/grub/stage1
/ GRUB > root (hd0,2)
/ GRUB > setup (hd0,2)
/ GRUB > quit
/root %
where hd0,2 was the value that the "find" command spat out as having my GRUB mbr. everything worked fine, it says it installed correctly so i rebooted. same error as before.

so, i looked around the forums and found this guide, and followed it's steps :
> 1. Boot with any live CD (I've done it with Ubuntu Live DVD)
2. Get a root shell -> Applications / System Tools / Root Terminal
3. Make a folder -> mkdir /mnt/ubuntu
4. Check the Ubuntu partition -> fdisk -l (Mine is /dev/hda4)
5. Mount the root partition of Ubuntu -> mount -t ext3 /dev/hda4 /mnt/ubuntu (replace /dev/hda4 by your Ubuntu partition determined at the step 4)
6. Chroot the mounted partition -> chroot /mnt/ubuntu
7. Restore Grub / the initial MBR -> grub-install /dev/hda
8. Exit the shell
9. Reboot

i got two errors during that walk through, and here's what they were :
> /root % chroot /mnt/ubuntu
chroot: cannot run command '/bin/zsh': no such file or directory

/root % grub-install /dev/sda
probing devices to guess BIOS drives. this may take a long time. 
seed : can't read /boot/grub/device.map : no such file or directory
grep : /boot/grub/device.map : no such file or directory
/dev/sda does not have any corresponding BIOS drive.

and, clearly, it didn't solve the problem. anyone have suggestions for what to try next?! :confused:

---

