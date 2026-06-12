---
title: "installed hardy, get 'invalid partition table' error"
date: 2008-05-31
forum: General Help
---

### Post by mooglinux on 2008-05-31
hi there, had xp up and running, but then one day booted up and got the error message 'ntldr missing'
so decided to install ubuntu in case there were any tools there that might be useful (i was gonna install it anyway, just had not gotten to it yet) so installed ubuntu and now i boot up and get the error "invalid partition table"
so i figure, maybe the bootloader is goofed up. so i tried to reinstall grub as per [these intructrions]("http://ubuntuforums.org/showthread.php?t=224351")and i get this output from grub: ```
setup (hd0,5)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0,5)"... failed (this is not fatal)
 Running "embed /boot/grub/e2fs_stage1_5 (hd0,5)"... failed (this is not fatal)
 Running "install /boot/grub/stage1 (hd0,5) /boot/grub/stage2 p /boot/grub/menu.lst "... failed
```
fdisk -l yields this:```
omitting empty partition (5)

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x3030302f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       30400   244187968+   f  W95 Ext'd (LBA)
/dev/sda2   *       15299       30400   121306783+   7  HPFS/NTFS
/dev/sda5               1       14933   119949228   83  Linux
/dev/sda6           14934       15298     2931831   82  Linux swap / Solaris

```
so now what do i do? should i try to use the xp recovery console to restore mbr, and then try intsalling grub after that?

---

### Post by logos34 on 2008-05-31
Use gparted to remove the 1st asterisk (i.e. the ext'd -- leave the one on windows sda2).

system>admin>partition editor

right-click sda1>manage flags>uncheck 'boot'

Reinstall grub to MBR with this diff:

root (hd0,**4**)
setup (hd0)

(hd0,4) = sda5 (linux root) -- grub starts counting frm 0

---

### Post by mooglinux on 2008-05-31
new problem tho, i run gparted and it sees the entire hard drive as unallocated.... :???:

---

### Post by logos34 on 2008-06-01
> **mooglinux said:**
> new problem tho, i run gparted and it sees the entire hard drive as unallocated.... :???:

That's happened to me too.  You will definitely need to get use TestDisk to fix the partition table. (see below--I was just about to post it when I saw your reponse)

(Afterthought: run sudo cfdisk if the livecd lets you, but I doubt if it will see anything  so you can toggle the bootable flag)

...
Looking over the grub shell output, I still don't understand why it says it detected menu.lst on (hd0,5), which is sda6, your swap partition!

You may need to use TestDisk to fix the partition table.  I've used it a number of time to correct errors after windows screwed it up.  Just be careful not to srite any changes to disk until your absolutely sure you know what's happening.  Read the [docs]("http://www.cgsecurity.org/wiki/TestDisk") and [this page]("http://www.users.bigpond.net.au/hermanzone/p21.html").

---

### Post by mooglinux on 2008-06-01
tried using cfdisk to take off the flag on one of the partitions that had it, but now i try to boot and the computer doesnt give any error message, it just sits there. guess its time to try testdisk

---

### Post by hal8000 on 2008-06-01
At least one partition has to be marked as (bootable) active. Your original problem was that two partitions were marked as bootable. You now probably have no partitions marked as active.
An alternative to testdisk is to boot with the live hardy CD and run fdisk or cfdisk from the terminal to fix this.

In your first post you have
setup (hd0,5)

this is wrong as partition 6 is you swap file.

The correct command from a grub shell for you is
root (hd0,4)  
setup (hd0)

as logos34 has already stated. Grub starts counting at 0, not 1.
Root (hd0,4) tells grub to install its config files on partition 5, your root partition, and setup (hd0) instructs grub to install into the mbr of the same hard disk.

---

### Post by mooglinux on 2008-06-02
Well i decided to just mount it from the live cd and copy over all the data, then format the whole thing from scratch. altho it wouldnt boot, accessing the data was no problem at all.

---

