---
title: "[SOLVED] Dual boot two SATA drives"
date: 2008-02-10
forum: General Help
---

### Post by gs110 on 2008-02-10
I recently got a second SATA hard drive so that I could dual boot Windows with ubuntu. I install xp on the new drive and was hoping to just set my ubuntu drive to be bootable first, from the bios, and be able to boot into windows through grub. The problem is that grub won't recognize the windows installation. I also found out that the bios is only recognizing the drive that is connected to the main sata connector on the motherboard. How can I get grub to recognize the windows drive?

---

### Post by Cavs23 on 2008-02-10
which isa your master drive?

---

### Post by gs110 on 2008-02-10
They're both on different cables, but I think the problem is that only two of the SATA inputs on the mobo are bootalbe. I think i'll just disconnect my dvd drive from a bootable spot and put it into a non bootable spot and replace it with the second hard drive. I'll get back to you when I test this.

---

### Post by gs110 on 2008-02-10
Grub still doesn't recognise the other hard drive, although the bios recognized the other hd and it gave me the option to put them in a raid array. Any ideas?

---

### Post by gs110 on 2008-02-11
Help please? :(

---

### Post by Tosa on 2008-02-11
I had similar problem when I attached the second SATA disk. Kubuntu messed up drives in *menu.lst* so I couldn't boot neither Kubuntu nor Win.
From your post I assume that you can boot to Ubuntu, but can't boot to Windows?

I suggest you should chek your drives: type in terminal

```
sudo fdisk -lu
```
Compare otput against /boot/grub/menu.lst. This is mine:

```
title        Ubuntu 7.10, kernel 2.6.22-14-generic
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.22-14-generic root=UUID=a9529e2e-fe08-43b5-8ce9-2d6a8b0b424a ro quiet splash nosplash
initrd        /boot/initrd.img-2.6.22-14-generic
quiet

title        Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.22-14-generic root=UUID=a9529e2e-fe08-43b5-8ce9-2d6a8b0b424a ro single
initrd        /boot/initrd.img-2.6.22-14-generic

title        Ubuntu 7.10, memtest86+
root        (hd0,2)
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:

title        Windows XP
root        (hd0,0)
makeactive
chainloader    +1
```
Kubuntu is on 3rd partition of the first drive (hd0,2), and Windows are on the first partition of the same drive (hd0,0). After I'd attached the new drive this one somehow became hd1, so I had to edit it manually.

HTH

---

### Post by gs110 on 2008-02-14
> From your post I assume that you can boot to Ubuntu, but can't boot to Windows?
Well I can boot into ubuntu if the main sata cable is connected to that hard drive, but I can only boot into windows if the main sata cable is connected to the windows hard drive.

My /boot/grub/menu.lst is
```
title		Ubuntu 7.10, kernel 2.6.23.12
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.23.12 root=UUID=7d2f9609-b4e3-4c59-80b2-e1d523d97cf1 ro quiet splash
initrd		/boot/initrd.img-2.6.23.12
quiet

title		Ubuntu 7.10, kernel 2.6.23.12 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.23.12 root=UUID=7d2f9609-b4e3-4c59-80b2-e1d523d97cf1 ro single
initrd		/boot/initrd.img-2.6.23.12

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=7d2f9609-b4e3-4c59-80b2-e1d523d97cf1 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=7d2f9609-b4e3-4c59-80b2-e1d523d97cf1 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
```

And the sudo fdisk -lu is
```
Disk /dev/sda: 250.0 GB, 250000000000 bytes
255 heads, 63 sectors/track, 30394 cylinders, total 488281250 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xe686f016

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   482223104   241111521   83  Linux
/dev/sda2       482223105   488279609     3028252+   5  Extended
/dev/sda5       482223168   488279609     3028221   82  Linux swap / Solaris

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00035721

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63   488392064   244196001    7  HPFS/NTFS

```

I'm not quite sure how to proceed.

---

### Post by malacoda on 2008-02-14
gs110,

I hope this isn't a silly question but did you add the Windows drive to your grub menu list?  

I ask because I don't see Windows listed anywhere in your grub menu list.

If your not new to  new to linux and/or grub then please disregard this post.  If you are new to it then this may help...

Grub won't just automatically 'see' your new drive and list Windows in its OS boot list at start up.

First off, take a look at the last 5 lines of the menu.lst in Tosa's last post.  You need similar Windows pointer.  Normally you can just edit the grub list with a text editor like gedit to add the lines.  

However, to do so you'll need to know you the drive and partition numbers for the drive and partition Windows is on.  In Tosa's case, Windows is installed on the first drive, first partition which is where the (hd0,0) comes from.

Second, in order to get the Grub OS list at start up you'll need to ensure your bios is set to boot your linux drive first since that's the drive that has grub installed to it's Master Boot Record.  If you've changed your bios boot order and it's set to boot the windows drive first you'll never see the Grub OS list at start up -- Windows will just automatically boot since it's the first disc read...

I may be wrong on this (still a bit of a noob myself) but the easiest thing to do may be to just reinstall Grub altogether while both drives are connected.  I can't remember if the Ubuntu install disc gives you the option of just running the grub installation step -- if it does then reinstalling grub should detect both OS's and take care of everything for you...

Good Luck,
Malac

---

### Post by gs110 on 2008-02-14
Thanks Malac, I didn't realize that grub didn't automatically find new drives/os's. :redface: I got it working now.

---

