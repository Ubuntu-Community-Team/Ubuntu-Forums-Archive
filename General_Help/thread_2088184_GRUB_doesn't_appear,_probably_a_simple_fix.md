---
title: "GRUB doesn't appear, probably a simple fix"
date: 2012-11-25
forum: General Help
---

### Post by cmalk on 2012-11-25
[FONT=Arial]I run a dual-boot Windows 7 / Xubuntu 10.04 machine. Recently Xubuntu crashed and refused to boot (straight to busybox) when I selected it from the GRUB menu. (Windows booted just fine.) I downloaded and ran Boot-Repair, which I believe fixed the problem with Linux, but I cannot check this because now the GRUB menu does not appear at all. The machine boots straight to Windows (which still works fine).

I tried holding Shift during boot-up but still no GRUB menu.

I have the output of Boot-Repair here:
[/FONT][FONT=Arial][http://paste.ubuntu.com/1385756/](http://paste.ubuntu.com/1385756/)

I think the system is booting from dev/sda2 instead of dev/sda6, or wherever GRUB is
located. Is there an easy way to change that?[/FONT]

---

### Post by oldfred on 2012-11-25
Welcome to the forums.

Boot-Repair initially could not mount the sda6 partition, just like grub could not to boot it. It needed (and may need again?) fsck to repair partition. 

It looks like Boot-Repair ran fsck and that did make some fixes, but it only installed the Windows boot loader.

If you run Boot-Repair again, does it also offer to install grub2's boot loader to the MBR from your install in sda6?

If not run fsck again.

       #From liveCD so everything is unmounted,swap off if necessary, change example shown with partition sda6 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sda6
#if errors: -y auto answers yes for fixes needing response see man e2fsck
sudo e2fsck -f -y -v /dev/sda6

---

### Post by cmalk on 2012-11-25
That did it! I just ran Boot-Repair again with the default options and now GRUB is back to normal. Thank you!

---

