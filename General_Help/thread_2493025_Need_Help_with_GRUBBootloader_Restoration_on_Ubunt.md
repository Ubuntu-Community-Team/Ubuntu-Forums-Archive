---
title: "Need Help with GRUB/Bootloader Restoration on Ubuntu 22.04 VM"
date: 2023-11-30
forum: General Help
---

### Post by imar18 on 2023-11-30
Greetings,
 As a long-time user of GNU/Linux, I’ve taken on a project involving  Ubuntu 22.04 for homework. I’ve successfully installed Ubuntu on a  VirtualBox virtual machine running on Windows 11. However, I’ve  encountered a challenge that I’m struggling to overcome.


 The task requires the following steps:
 
[LIST=1]
[*]Find and remove the GRUB/Bootloader. 
[*]Use the Ubuntu live ISO in recovery mode to restore the bootloader. 
[/LIST]

 In an attempt to complete the first step, I removed the file located at ```
/boot/grub/grub.cfg
``` I’m unsure if this was the correct file to remove, but since doing so, Ubuntu will no longer boot.

 

 Despite numerous attempts, various tutorials, extensive searches, and  even consulting AI chatbots, I’ve been unable to find a solution to recover the grub.
To carry out this task, I created a clone of the virtual machine. Could this possibly be the source of the problem?


 I’m eager to learn and would greatly appreciate any guidance or suggestions. 

This was one of my attempts to recover the bootloader:
```
[COLOR=#343541][FONT=Söhne]sudo fdisk -l 
sudo mount /dev/sda3 /mnt  
sudo mount --bind /dev /mnt/dev 
sudo mount --bind /proc /mnt/proc 
sudo mount --bind /sys /mnt/sys  

sudo chroot /mnt  
sudo grub-install /dev/sdX  
grub-mkconfig -o /boot/grub/grub.cfg  
sudo update-grub  
exit  

sudo reboot[/FONT][/COLOR]




```

---

### Post by oldfred on 2023-11-30
There must be a million posts here and in other forums and question & answer sites.

But grub is installed in multiple places and varies a bit whether old BIOS or new UEFI boot install.

GRUB 2 - GRand Unified Bootloader has three main parts plus a boot loader installed to the MBR or ESP if UEFI.

1. /etc/default/grub - the file containing GRUB 2 menu settings.
2. /etc/grub.d/ - the directory containing GRUB 2 menu creating scripts.And a place for totally custom entries 40_custom.
3. /boot/grub/grub.cfg - the GRUB 2 configuration file, not editable.

UEFI does not have boot files in gpt's protective MBR, but has files in the ESP -  efi system partition.
And UEFI has UEFI boot entries to load grub.

How the repair or reinstall grub varies if UEFI or old BIOS type install.

[https://www.gnu.org/software/grub/manual/grub/grub.html](https://www.gnu.org/software/grub/manual/grub/grub.html)
[https://www.happyassassin.net/posts/2014/01/25/uefi-boot-how-does-that-actually-work-then/](https://www.happyassassin.net/posts/2014/01/25/uefi-boot-how-does-that-actually-work-then/)

---

### Post by MAFoElffen on 2023-12-01
Is the VM setup as legacy boot or UEFI boot? There is goig to be a lot of variables, based on how you installed the original VM.

These instructions assume that it was installed as legacy boot, which is VirtualBox'es default, unless you chnaged that for the VM to UEFI. Do this...

Connect the ISO in the CDROM Virtual device of VBox. Set the boot order to the CDROM drive as first, before the Virtual disk... Boot

Use "Try". Start a terminal.
```

sudo su -
lsblk -e7 -o name,label,size,fstype,model

```
Look at the output to determine which partition to mount... You said /dev/sda3... Did it say fstype ext? If so, then use that to mount to (later down)

If it says (anywhere) vg-something, stop and post back. aYou would need different instructions. Look to see if it there is a /dev/sda1, and if it is fstype vfat... If so, stop and post back...

Then determine if it is UEFI or Legacy boot
```

 -d /sys/firmware/efi ] && echo "UEFI Firmware mode" || echo "Legacy mode (alias CSM alias BIOS mode)"

```
Take not of this...
```

mount /dev/sda3
mount --make-private --rbind /dev /mnt/dev 
mount --make-private --rbind /sys /mnt/sys
mount --make-private --rbind /proc /mnt/proc
mount --make-private --rbind /run /mnt/run
mkdir /mnt/run/lock # This may say it already exists
chroot /mnt /usr/bin/bash --login
mount -a

```

What you did was to delete just /boot/grub/grub.cfg, right? To rebuild that you would just do
```

update-grub

```
What you were told to do was to remove Grub, then later re-install it.

To do that, you would this (for legacy)
```

apt remove grub-pc

```
Later to install it you would do 
```

apt install -y grub-pc
grub-install /dev/sda
update-grub

```

If you had UEFI boot, then you would remove it via
```

apt remove -y grub-efi-amd64 grub-efi-amd64-signed shim-signed

```
Then to reinstall
 ```

apt remove -y grub-efi-amd64 grub-efi-amd64-signed shim-signed
grub-install --target=x86_64-efi --efi-directory=/boot/efi --bootloader-id=ubuntu --recheck --no-floppy
update-grub

```
When done
```

exit
umount /mnt
reboot

```

---

