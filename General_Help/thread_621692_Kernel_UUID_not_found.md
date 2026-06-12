---
title: "Kernel UUID not found"
date: 2007-11-24
forum: General Help
---

### Post by aleph4 on 2007-11-24
When starting up it takes a really long time and then it finally loads and when in verbose mode says:
Warning /dev/disk/by-UUID/ (my hd's uuid here) not found 
and gives some tips to check for missing files and drops me to a shell (initramfs)

in /proc/cmdline it says root=UUID=(my hd's uuid here)
It says the same UUID as the one not found. I checked my fstab and tried using
udevtrigger and sudo vol_id /dev/sda1 and nothing.

Dosen't make any sense because all UUIDs are the same and after looking at /dev/disk/by-UUID the file is there for that UUID

Any suggestions?

---

### Post by rbmorse on 2007-11-24
Check 

/boot/grub/menu.lst 

and make sure the UUID for the kernel's partition is  correct there (or at least the same as shown in fstab,  and that shown when you run 

blkid

from a term window.

---

### Post by aleph4 on 2007-11-25
I checked and they are the same 

/dev/sda1: UUID="d3eb92f9-435c-4423-ab33-1b56968aae7a" SEC_TYPE="ext2" TYPE="ext3"

and 

title           Ubuntu 7.10, kernel 2.6.22-14-generic (on /dev/sda1)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=d3eb92f9-435c-4423-ab33-1b56968aae7a ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-generic
savedefault
boot


..

I was looking and there's a chance (unless somehow i'm looking at this wrong) that the entire /proc folder is empty. this would explain why it tells me to check /proc/cmd-line

im going to try to recreate this but i doubt it'll work... ill probably just have to reinstall

---

