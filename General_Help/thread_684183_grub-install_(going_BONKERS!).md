---
title: "grub-install (going BONKERS!)"
date: 2008-01-31
forum: General Help
---

### Post by GutsyVirgin on 2008-01-31
As my handle implies, I am a total newb to Ubuntu and LInux altogether. I've managed to educate myself with some pretty useful commands and knowledge, though obviously still have a LOT to learn as proven by my current head-scratching dilemma.

So here's my problem. I Have **Windows XP Pro** on one side of my laptop which I unfortunately need for my engineering classes, and recently installed **Ubuntu 7.10** on the other side making my computer **dual boot with Grub**. Everything was working great... for awhile.

Then I decided to go ahead and create a **new partition in Windows** using the remaining undefined region of my hard drive. Apparently Gutsy didn't like my new Windows-made partition and decided to stop working and booting all together giving me the infamous **Grub Error 17**. I've booted from the Live CD numerous times scouring the net searching for an answer to my problem.

I've tried every trick and command I can find and I've gotten all the errors you can imagine. So after creating the partition that caused the error, I proceeded to delete it again and** then used the Linux Partition editor on the Live CD to resize and move my partitions around**. I've now got the following partitions according to: "fdisk -l"[INDENT]root@ubuntu:~# _**fdisk -l**_

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xba2cba2c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       10823    86935716    7  HPFS/NTFS
/dev/sda2           12129       12161      265072+  82  Linux swap / Solaris
[B]/dev/sda4       10824    12128    10482412+  83  Linux
[/B]
Partition table entries are not in disk order

Disk /dev/sdb: 1998 MB, 1998585344 bytes
255 heads, 63 sectors/track, 242 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         242     1943857    b  W95 FAT32
root@ubuntu:~# 
[/INDENT]Since that didn't work either. I tried using the **Windows XP cd to enter repair mode** where I ran: "**fixmbr**" and "**fixboot**" Neither of which worked. As you can see I've tried just about everything my puny Linux brain can imagine and **NOTHING HAS WORKED!**

I would love to hear anyones daring attempt to help me with this daunting issue. I really want to turn pro at Linux and master these administrative commands. And for future notice. How should I go about creating or manipulating partitions without screwing up my MBR or Grub?

[COLOR=DarkSlateBlue]*I greatly appreciate your help for reading all this. Thank you so much for any help or suggestions you're willing to offer. I will post again immediately after I solve the problem and give credit where credit is due. Thanks.*[/COLOR]

**_The Simple Version:_**
- Windows XP & Gutsy Gibbon Dual Boot with Grub
- Created new partition in XP with unused HD space
- Grub stopped working (Error 17)
- Searched far and wide trying every trick I could find but nothing works
- Need some more robust (sure fire) ways to fix my GRUB
- Thanks very much for your help. Will reply when fixed.
[COLOR=DarkOrange]
Matthew[/COLOR]

---

### Post by harold4 on 2008-01-31
[Reinstall GRUB]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")

---

### Post by imtheguru on 2008-01-31
> ... create a new partition in Windows using the remaining undefined region of my hard drive. Apparently Gutsy didn't like my new Windows-made partition and decided to stop working and booting all together giving me the infamous Grub Error 17.Error 17 means that the known partition layout does not match the one reported by the bios. They won't match, as you've made changes from another OS--that's working as intended.

Start with the liveCD. Mount your root (/) on a mount point say /mnt/rootpart with correct filesystem and rw access.

Override udev and bind /dev and /proc to a location under /mnt/sysimage, copy mtab:
$ sudo mount -o bind /dev say /mnt/rootpart/dev
$ sudo mount -o bind /proc say /mnt/rootpart/proc
$ sudo cp /proc/mounts say /mnt/rootpart/etc/mtab

chroot to this new mount point 
$ chroot /mnt/rootpart /bin/bash

You have now left the safety of the live cd and are working off your linux install.

You can now use /sbin/grub-update to update your grub conf. If grub-update doesn't change the contents of menu.lst, edit it by hand.

Finally move the new grub information into the master boot record--if that's where you installed it the first time--using grub-install. If that fails, use grub and provide the correct paths for
> root hd(x,y)
> setup hd(x)
where x is the drive # (starting from 0) and y is the partition number minus 1.

---

### Post by GutsyVirgin on 2008-02-13
I figured it out. It might not be the most ideal, but it worked. I used the Windows Repair Install function to reinstall a repaired copy of Windows. Then I fixed the MBR with the Windows tool when booting from the CD (mostly as a precaution), then I booted from the Ubuntu Live CD and used fdisk to reorder the partitions. This then screwed up my Grub for booting into Ubuntu, but Windows was fixed. So then I figured out how to edit the Grub during boot, although it wasn't the permanent fix I was hoping for. Finally, I found this WONDERFUL command for getting access to my root.

gksudo nautilus

Enter the Admin Password. EUREKA!! I finally got administrative access to my root and was able to edit my Grub "menu.lst" to reflect the options I wanted available from the bootscreen. Now it works like a charm and the Grub points to all the correct partitions once again.

Still don't know if I could repeat this fix if I needed to though, hehe. Hope this helps someone else out there. Just remember that command. It's by far the most useful command I've learned in Ubuntu to date!

---

