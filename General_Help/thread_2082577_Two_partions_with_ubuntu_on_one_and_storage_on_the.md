---
title: "Two partions with ubuntu on one and storage on the other?"
date: 2012-11-09
forum: General Help
---

### Post by LilLZ on 2012-11-09
Hello. I have a 1TB external hard drive... I never, ever plan to use that much storage for ubuntu, so the rest would be a waste and then I can't use the drive with my mac or pc.... Will it still work and boot on computers I plug it into if I partition the drive to two separate partions, one for Ubuntu, and one for general storage?

---

### Post by BertN45 on 2012-11-09
I assume you want to boot Ubuntu from the external hard drive. Yes it will be possible to create two partitions. You could use windows to create both partitions and format the data partition with e.g. ntfs and you could use and format the other free partition during the installation of Ubuntu.

---

### Post by LilLZ on 2012-11-09
And the computers I want to boot it off of will see the bootable partition and use that? Most computers I do this sort of stuff with just see the hard drive, not the partitions...

---

### Post by ibjsb4 on 2012-11-09
You can just shrink (resize) the Ubuntu partition.

[http://www.dedoimedo.com/computers/gparted.html#mozTocId335513](http://www.dedoimedo.com/computers/gparted.html#mozTocId335513)

You have gparted on the live CD.

---

### Post by 2F4U on 2012-11-09
> **LilLZ said:**
> And the computers I want to boot it off of will see the bootable partition and use that? Most computers I do this sort of stuff with just see the hard drive, not the partitions...

By default those computers are probably set to boot from a different drive, so you have to tell them to boot from the external drive. This can be done by either changing the boot order in the BIOS, or by accessing a temporary BIOS boot menu at boot time. On some computers the key to access this temporary boot menu is F11 or F12, but this is vendor specific.

---

### Post by LilLZ on 2012-11-09
Yeah I know that, but when you go into a boot menu, it usually refers to the drive by its serial number or something odd like that, not the partitions you have created... So will it boot from Ubuntu drive?

---

### Post by oldfred on 2012-11-09
Computers boot from the MBR or very first sector on a drive, not really from a partition. But the MBR generally then refers to more boot code in a partition.

So when installing to an external drive you have to be sure to install grub2's boot loader to the MBR of the external drive.

Install to external drive 11.04. Also any second drive.
Installer version has not changed much so still a good guide except I do not recommend the separate /boot for most systems. Older systems may need it. And some with very large / (root) partitions. BIOS/MBR not for UEFI
[http://www.linuxbsdos.com/2012/07/23/dual-boot-ubuntu-12-04-and-windows-7-on-a-computer-with-2-hard-drives/](http://www.linuxbsdos.com/2012/07/23/dual-boot-ubuntu-12-04-and-windows-7-on-a-computer-with-2-hard-drives/)
Installing Ubuntu in Hard Disk Two (or more) internal or external Lots of detail - now alternative (text based) installer
Maverick screens shown, other versions have slight difference in screens but process is the same.
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)
p24/041.png Shows combo box to select where to install the grub2 boot loader.
Where Do You Want To Install GNU/GRUB boot loader?
[http://members.iinet.net.au/~herman546/p24/041.png](http://members.iinet.net.au/~herman546/p24/041.png)

---

### Post by LilLZ on 2012-11-09
I've installed and booted to an external drive before, but just with the whole drive dedicated to ubuntu rather than having only a part of it. Anyways I'll check those links out to see if I can get grub on the MBR. So, if I do that, I can have a drive of which I speak, right?

---

### Post by BertN45 on 2012-11-10
One bootable partition covering the whole drive or two partitions with only one bootable, I see no difference. Keep it simple.

---

### Post by HiImTye on 2012-11-10
if you do want to make separate partitions, then keep in mind file system restrictions and file system compatibility. it's not recommended to use the ntfs-3g driver to write to drives in Ubuntu, and FAT32 comes with a file size limit (so if you want to store, for instance, a .iso of a DVD-ROM image, it has to be smaller than that). I would do some research before committing to a partition scheme.

you can do all of the work of formatting, etc, within the Ubuntu LiveCD, just make sure you select 'something else' from the install options

---

### Post by oldfred on 2012-11-10
I have installed to flash drives the same way. Multiple partitions on an external device.

A full install of Ubuntu in one partition and data in other partitions. I just have not used NTFS except on one flash drive that I created for Windows repairs. But It also has another partition for booting repair ISOs with grub2.

---

### Post by LilLZ on 2012-11-10
Alright it sounds like it'll work, so I'll just go for it.

---

