---
title: "Shrink partition ?"
date: 2019-02-20
forum: General Help
---

### Post by garyed on 2019-02-20
I have a laptop that I dual boot with Ubuntu 18.04 & Windows 10. Since I rarely use windows I only left a small partition for it & the majority of the drive is left for Ubuntu. Now I need more space for my Windows partition for a particular program & I need to get back some of the extra space that I don't need from the Ubuntu partition. I don't want to have to reinstall Ubuntu but Gparted will only let me shrink from the back of the partition & not let me move the partition from the front. I want to keep Windows OS with the programs on just one partition & where that partition ends the Ubuntu partition begins. Is there any way to slide the used side of the Ubuntu partition towards the back & shrink from the front instead of the back?

---

### Post by oldfred on 2019-02-20
You shrink from the end, and then move right, normally.
Is this UEFI with gpt or BIOS with MBR?

If MBR you may also have to move start of extended partition.
Post this:

NTFS typically wants 30% free to run well. At 10% free, you just about cannot run a defrag as you have no working room.

---

### Post by garyed on 2019-02-21
It's UEFI /gpt .
I know how to shrink from the end but in Gparted but how do i move it to the right afterwards? The order is the Windows partition & then the Ubuntu partition. After I shrink the Ubuntu partition then the open space to the right will be unallocated.  I would then need to switch places with the Ubuntu partition & the unallocated space so the Windows partition could then be expanded into the unallocated space. Is that doable?

---

### Post by garyed on 2019-02-21
Well I shrunk the Ubuntu partition, then moved it to the right, then expanded the windows partition into the unallocated space. Everything looked good in gparted but I evidently lost the bootloader. I've got the space I need but it now boots directly into windows & can't get back into Ubuntu. Before GPT/UEFI I had no problem reinstalling Grub but I have no idea how to do it now with Windows 10 UEFI /GPT. I'll do some googling but any help appreciated.

---

### Post by oldfred on 2019-02-21
New users often find Boot-Repair easier. If it works no need to post report.
Just start up Ubuntu live installer and add Boot-Repair using ppa.

       Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot, only use ppa download into Ubuntu live installer.
May be best to see details, use ppa version with your live installer or any working install,  not older Boot-Repair ISO:
Please copy & paste link to the Boot-info summary report ( do not post report), the auto fix sometimes can create more issues.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

 Note that grub only boots working Windows. Or if Window need chkdsk or is hibernated then grub will not boot it, but if UEFI install, you should still be able to boot from UEFI boot menu.
Windows updates also turn fast start up back on which is just hibernation. That then grub will not boot it, or any NTFS partitions will not mount read/write in Ubuntu.

---

### Post by garyed on 2019-02-21
Thanks  for all the info & ideas,
I finally got it to work using an Lubuntu 18.04 live usb stick.
I found a good tutorial here:  [https://askubuntu.com/questions/88384/how-can-i-repair-grub-how-to-get-ubuntu-back-after-installing-windows](https://askubuntu.com/questions/88384/how-can-i-repair-grub-how-to-get-ubuntu-back-after-installing-windows)     
These are the actual steps that worked for me.
1 - I had to make sure my BIOS was set to boot EFI & also that the USB live boot disk was EFI compatible & then boot up with it.  
2 - run: fdisk -l to find my Ubuntu install partition (/dev/sda7) & EFI partition ( /dev/sda1) .
3 - Mount Ubuntu partion: sudo mount /dev/sda7
4 - Bind mount the dirs:    for i in /sys /proc /run /dev; do sudo mount --bind "$i" "/mnt$i"; done
5 - Mount EFI partition:   sudo mount /dev/sda1 /mnt/boot/efi
6- chroot into Ubuntu system:   sudo chroot /mnt
7 - run:  grub-install /dev/sda   (after that finished then run)    update-grub
8 - exit & reboot  
Seems like the developers could make it a lot easier but to do with less steps but it worked & that's what counts.

---

