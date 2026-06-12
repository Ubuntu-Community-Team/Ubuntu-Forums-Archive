---
title: "Grub Nightmare"
date: 2007-08-14
forum: General Help
---

### Post by Page on 2007-08-14
I had to reinstall Windows XP tonight. I knew the MBR would be overwritten, so I gave the [grub restore guide](http://ubuntuforums.org/archive/index.php/t-24113.html)  a quick study and went ahead with the reinstall.

Later, I tried to restore grub from the ubuntu livecd.  The grub restoration process went as expected  (My Stage 1 is on hd1,0 ) so that is what I set the root to use. The process claimed to finish successfully. 

However, when I tried to reboot, grub was nowhere to be found and windows still started automatically. Windows is on hd0. On my second attempt I tried to set the root to hd0,0, but when I tried to setup I got "grub error 17: could not mount that partition."

I tried fixing the mbr with supergrub, but that didn't work either. (although supergrub did let me boot into Linux)


Am i totally screwed, or is there something else that I can try?

---

### Post by wieman01 on 2007-08-14
To format the MBR you need to get hold of a Windows 98 boot CD. Then type this (DOS):

> fdisk /mbr

---

### Post by rbmorse on 2007-08-14
I think the problem is that the MBR the BIOS wants to boot from is not the on the same drive your Linux root is, so try this: 

Boot from a LiveCD or Gparted or RescueCD or similar and get to a terminal. Then it's: 

sudo grub

find /boot/grub/stage1       

just to confirm how drives are enumerated. It can change depending on the environment.  Take the result from the find command (should be (hd1,0) if things stay consistent and: 

root (hd1,0)                <  Use the values returned by the find command 

then

setup (hd0)             <  write GRUB's IPL to the MBR of the drive that BIOS boots from. Unless you have manually entered some remapping commands, the drive Windows installed itself to will be (hd0). 

quit, exit, reboot

---

