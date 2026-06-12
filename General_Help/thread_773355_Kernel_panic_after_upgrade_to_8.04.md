---
title: "Kernel panic after upgrade to 8.04"
date: 2008-04-28
forum: General Help
---

### Post by trackzilla on 2008-04-28
Just upgraded my Thinkpad T61 from Feisty to Hardy.  At the Grub options I select 'Ubuntu 8.04, kernel 2.6.24-16-generic' and receive the following:

Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(0,0)

The machine dual boots Vista (preloaded) and Ubuntu.  Any suggestions?  Thank you in advance for the help.

---

### Post by amohanty on 2008-04-29
The problem may be that grub has the wrong partition type specified for boot. Occassionally grub does not agree with BIOS and makes up its own mind, usually for the worse. 

When you get to the grub prompt, press 'e' to edit the boot options and try changing the entry that says (hdx,y).
[http://www.gnu.org/software/grub/manual/grub.html#Device-syntax](http://www.gnu.org/software/grub/manual/grub.html#Device-syntax)

Also if you post your partition layout, I can probably suggest sane values to use.

AM

---

### Post by trackzilla on 2008-04-29
I used the directions from the following post the last time I had problems and it worked.  I tried them again and could not resolve the issue; the step "sudo update-grub" could not resolve ubuntu.

[http://ubuntuforums.org/showthread.php?t=647568&page=1](http://ubuntuforums.org/showthread.php?t=647568&page=1)

Pressing 'e' when grub loads shows me the following:

root (hd0,3)
kernel /boot/vmlinuz-2.6.24-16-generic root=UUID=dc30d344-3720-4064-9310-->

If I change the 3 in root (hd0,3) to 4 or 2, I receive an error stating grub cannot boot.  When I keep it selected on (hd0,3) I receive the following:

Filesystem type is reiserfs, partition type 0x83
kernel /boot/vmlinuz-2.6.24-16generic root=UUID=dc30d344-3720-4064-9310-f3115-ca4e53c ro quiet splash
[Linux-bzImage, setup=0x2a00, size=0x1ce278]

[234.638672] Kernel panic - not syncing: VFS: Unable to mount root fr on unknown-block(0,0)

---

### Post by amohanty on 2008-04-30
AFAIK you cannot boot off of reiserfs or xfs. Only ext2 or ext3 works for me. This means that your /boot (if it is a separate partition) or / _needs_ to be ext2/3.

Can you possibly post your partition layout?

---

### Post by trackzilla on 2008-04-30
I believe my partition setup is the following:

sda1 = hidden IBM recovery partition
sda2 = Vista Ultimate
sda3 = swap
sda4 = Ubuntu 8.04

If this is not sufficient, can you please identify the commands I can run in the terminal (via a live cd) to identify the partition setup.

Thanks.

---

