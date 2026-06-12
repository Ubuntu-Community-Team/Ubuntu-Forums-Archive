---
title: "Clone an SD card win an embedded OS with dd"
date: 2018-03-06
forum: General Help
---

### Post by giobaxx on 2018-03-06
A collegue asked me how we can can clone an SD.  For the moment  i know only that in that SD card there is a Bootable Operating System. Probably it's an embedded to OS.

I though to use the command dd and if i want to clone the SD card to a file is correct this command below?

[I][B]dd if=/dev/sdc    of=/home/user/embeddedOS.img  ?

[/B][/I]there is a best practice about how to set some option in dd to make it works better?  

if later i wanted to clone the file img to an another SD DISK i use this

***dd   if=/home/user/embeddedOS.img  o***[I][B]f=/dev/sdc

[/B][/I]and  it will be Bootable as it was the original or i have to add some option?

---

### Post by TheFu on 2018-03-07
**dd** is certainly 1 method.  I'd add a blocksize to make it faster.  bs=1M should do it.
Any of the image-based backup tools should work.
* ddrescue
* partimage
* clonezilla
* 20 others.
If you know the file system type, using a file-system aware backup/recovery tool might be much faster.  Something like **fsarchiver**.  

You'll need to handle any partitioning outside/manually.  Something like sfdisk or dumping a machine readable partition table info using fdisk, parted might be what you want.  Of course, if you do this, then the source and target should be the same size.

With a basic understanding of the layout on disk for different logical disk objects, you can be highly efficient in doing this.
* partition table
* partitions
* any volume management (LVM/ZFS/btrfs)
* file systems

Unix systems really just care that file systems appear to be where they need to be - by name.  /boot/, /, /var, /usr, are the most important.  And the boot controller (grub/lilo) needs to be in the correct place after the partition table.  GPT partition tables are located at the beginning AND the end of a physical disk.

anyways - sudo dd if=   of=  bs= .... is probably what  you want.  May want to flush any buffers after, if you are in a hurry.

---

