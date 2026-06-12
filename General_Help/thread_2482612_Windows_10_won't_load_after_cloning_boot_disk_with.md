---
title: "Windows 10 won't load after cloning boot disk with Windows 10 and Ubuntu 22.10"
date: 2023-01-05
forum: General Help
---

### Post by xandrewx86 on 2023-01-05
Hi I had a 500gb nvme ssd that had Windows 10 and Ubuntu dualboot and when I cloned the disk to a new 1tb nvme ssd using Macrium Reflect within Windows I am no longer able to go into Windows anymore but Ubuntu works just fine. When grub bootloader shows up and I select Windows 10 it gives me this error message:

error: Secure Boot forbids loading module from (hd8,msdos5)/boot/grub/x86_64-efi/parttool.mod.
error: can't find command -drivemap'.
error: bad shim signature.

Press any key to continue...

I have grub customizer installed on Ubuntu and I had a custom boot loader screen before but after cloning the disk it seemed to reset. I googled these error messages and they seem to be easy to fix but I wanted to make sure to get a reliable solution by asking here since Windows 10 is my main OS

---

### Post by TheFu on 2023-01-06
Seems like an MS-Windows boot question and perhaps a license and signed driver question.

---

### Post by yancek on 2023-01-06
Does it boot if you turn off Secure boot?  The module parttool.mod is in the /boot/grub/x86_64 directory.  Do you have a file named shimx64.efi in your /boot/efi/ubuntu directory?  You may need Grub to use that.  Just guessing here as I'm not sure about windows with 2 instances on the same computer?

---

### Post by xandrewx86 on 2023-01-06
I gave up and swapped back to my 500gb nvme :lol: I guess using Macrium Reflect in Windows to clone was definitely NOT the solution to upgrade to a bigger ssd. Until I find a solid procedure on how to copy partitions over to a bigger ssd, resize them and manipulate to accomodate to a bigger drive while still being bootable to Windows 10 and Ubuntu (I think I read gparted or clonezilla or dd command does a perfect byte by byte copy of partitions, but they are very complicated and will need me to take time off to learn) I will keep this 1tb nvme stored away for the future or if my 500gb gets full and will need additional space. 

Thanks anyway.

---

### Post by TheFu on 2023-01-06
Actually, they are really dumb, which means it is a 50% chance of trashing the wrong disk. But if you are careful, moving all the bytes from A ---> B is really bonehead.  

Any tool that does that, unmolested, can be used.  I routinely use 'cp', for example, but have used dd, ddrescue, mkusb, and a few others over the decades.  The Unix 'cp' doesn't mess with files, unlike the 'copy.exe' in other OSes, so it is fine to use.  Of course, the user needs to understand the way that devices are named under Linux to perform this correctly.

If you run 
```
lsblk -e 7 -o name,size,type,fstype,mountpoint
```
with both drives connected and clearly point out which disks you want as the source and target for cloning, I'll happily post an exact command line.  Both cannot be in use, so you'll need to boot from 'alternate media' ... use any Ubuntu installer on a USB flash drive in "Try Ubuntu" mode.

When done, the older drive must be removed before booting from the newer drive.  Duplicate UUIDs is bad. That's why 1 must be removed.

---

