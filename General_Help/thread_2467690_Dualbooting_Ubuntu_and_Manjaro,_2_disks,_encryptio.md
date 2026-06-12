---
title: "Dualbooting Ubuntu and Manjaro, 2 disks, encryption and slow boot"
date: 2021-10-05
forum: General Help
---

### Post by fredlb on 2021-10-05
Not sure this is the right forum but here goes anyway:
I'm dualbooting Ubuntu 20.04 and Manjaro. I've installed these OS on two separate disks where the Ubuntu install resides on an encrypted disk (setup using the normal install process for Ubuntu).
It works but I'm having two issues:
First issue
Booting into Ubuntu is very slow, much slower than before I installed Manjaro on the other disk. It starts to get slow after I type in the password to unlock the drive. A solid 3-4min to even get to the login screen. After that, everything is normal.

Second issue
Whenever I perform any kind of updates to the kernel in either of these systems, menu items in grub tend to disappear. I have to boot to Manjaro, manually mount the encrypted drive and perform an update-grub to get them back.

Here are my disks:
```

Manjaro drive
Disk /dev/nvme0n1: 953,89 GiB, 1024209543168 bytes, 2000409264 sectors
Disk model: INTEL SSDPEKNW010T8                     
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: 0F44CF33-3638-7849-AB38-211BF1B80BE3

Device          Start        End    Sectors   Size Type
/dev/nvme0n1p1   4096     618495     614400   300M EFI System
/dev/nvme0n1p2 618496 2000397734 1999779239 953,6G Linux filesystem



This is the encrypted drive with Ubuntu
Disk /dev/sda: 465,78 GiB, 500107862016 bytes, 976773168 sectors
Disk model: Samsung SSD 870 
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: 00DEB3E0-48FB-436C-813C-1F9FB1756AB4

Device       Start       End   Sectors   Size Type
/dev/sda1     2048   1050623   1048576   512M EFI System
/dev/sda2  1050624   2549759   1499136   732M Linux filesystem
/dev/sda3  2549760 976771071 974221312 464,6G Linux filesystem

```

It feels like I got something wrong in this setup but I just don't know what. I'm simply trying to have two OS installed on separate drives with one of them encrypted. I'm fine with reinstalling everything as long as I know that there is a solution to this.

---

### Post by dragonfly41 on 2021-10-05
I make a suggestion which is "off piste" ..
It is to try installing Refind to extend boot options ..

but the encrypted drive worried me so I checked if refind works in that mode

[https://bbs.archlinux.org/viewtopic.php?id=263686](https://bbs.archlinux.org/viewtopic.php?id=263686)

If you cannot find a fix, I would try refind .. it can be installed easily and uninstalled just as easily without affecting your normal grub.

You can even create a custom UI by hacking refind.conf.

I use it in multi boot mode (Windows plus other Ubuntu installations).

P.S. Refind installs into /boot/efi/EFI/refind/ ..

---

### Post by Dennis N on 2021-10-05
Since your computer is UEFI, I would think the easy way to deal with these two is to chainload to Ubuntu EFI from Manjaro grub menu using a custom menu entry. Ubuntu will handle its own decryption as usual and should boot up as before.

This would also fix the update problem you describe that's being caused by kernel updates.

---

### Post by grahammechanical on 2021-10-05
You have two drives. Each with its own distribution of Linux and each distribution has its own bootloader (Grub) on its drive. Every time a distribution upgrades the Linux kernel or Grub the boot menu on that drive is rewritten. We have to choose a drive to have boot priority and have that drive's Grub in charge of booting.

When there is an update on the other drive that upgrades the Linux kernel we need to load the distribution that is in charge booting and run update-grub otherwise the new kernel in the other distribution will not be listed in the Grub boot menu.

This is normal. It has to become part of the way we work when running more than one install of Linux. 

Regards

---

### Post by Dennis N on 2021-10-05
> When there is an update on the other drive that upgrades the Linux kernel we need to load the distribution that is in charge booting and run update-grub otherwise the new kernel in the other distribution will not be listed in the Grub boot menu.
This is solved by chainloading - Ubuntu boots from is own grub menu which is updated along with the kernel update.

---

### Post by oldfred on 2021-10-06
I have multiple Ubuntu installs and use 40_custom, so I do not have to boot every install to update with new kernel in main working install.

[https://help.ubuntu.com/community/Grub2/CustomMenus](https://help.ubuntu.com/community/Grub2/CustomMenus)

sudo nano -B /etc/grub.d/40_custom
Then do:
sudo update-grub

See 6.5 on configfile details
[https://www.gnu.org/software/grub/manual/grub/grub.html#Multi_002dboot-manual-configSee](https://www.gnu.org/software/grub/manual/grub/grub.html#Multi_002dboot-manual-configSee) 6.5 on configfile details
[https://www.gnu.org/software/grub/manual/grub/grub.html#Multi_002dboot-manual-config](https://www.gnu.org/software/grub/manual/grub/grub.html#Multi_002dboot-manual-config)
I now use labels so I can see which install is which.

Typical entry:
```
menuentry "Ubuntu 20.04 focal_b  (on /dev/sda5)" {
    set root=(hd1,gpt9)    search --set=root --label focal_b --hint hd1,gpt5
    configfile /boot/grub/grub.cfg
}

```

Or you can chainload to the other install's grub in the ESP.

```
menuentry "Fedora UEFI" {
  search --file --no-floppy --set=root F496-1330
  chainloader (${root})/efi/fedora/grub.cfg
}

```


UEFI configfile
[https://askubuntu.com/questions/1002789/3-oss-win10-and-ubuntu14-04-on-drive-sda-and-ubuntu-16-04-on-sdb](https://askubuntu.com/questions/1002789/3-oss-win10-and-ubuntu14-04-on-drive-sda-and-ubuntu-16-04-on-sdb)

example UEFI configfile:
[https://askubuntu.com/questions/1205982/how-make-external-usb-disk-bootable-for-bios-and-uefi](https://askubuntu.com/questions/1205982/how-make-external-usb-disk-bootable-for-bios-and-uefi)

---

### Post by fredlb on 2021-10-11
Having a separate menu entry worked great! Thanks a lot all!
I also solved the slow boot problem which was unrelated:
In my /etc/fstab I had a line for /boot/efi on an UUID that was not there. So I assume that it was looking for something during boot until it timed out. I just commented that out and its fast again :)

---

