---
title: "How to unmount /dev/sda4 (/home) without live cd/usb."
date: 2014-05-23
forum: General Help
---

### Post by andrew123ast on 2014-05-23
Well, heres the problem, my brother trashed my old laptop, but we have the same hdd, so I put my hdd in his laptop since his was fine except it had a shot hdd. Everything worked fine, excpet his bios is an old version where you cant boot from usb. so im ****ed unless there is a way to resize my /home partition as root. And yes I can get on the root account. And please hurry, I only have 1 gig left on my home partition.
Edit: I have 28.45 gb unallocated.
I want to change /dev/sda1 from 103.64 gb to 100.00.
       I want to change /dev/sda4 from 15.00 to everything thats left.

---

### Post by andrew123ast on 2014-05-23
OK new update, I restarted my computer so I could try recovery mode, and it won't work. It won't even take me to grub it just says non system disk or disk error replace and strike any key when ready.

---

### Post by sudodus on 2014-05-23
Work-around:

Create a data partition of the unallocated space and move what is easy to move there, for example multimedia files. Then your home partition should get a lot a free space again. You can make symbolic links to directories in the new partition if you wish, and you can add a line in /etc/fstab to mount the data partition.

This is actually my configuration I made the partition for multimedia files, but now I use it for all big files and directories, and I have a separate backup of this partition.

The problem:

You cannot unmount an active partition and the home partition is active. So you must boot from another partition (or drive). If you cannot boot this computer from CD/DVD or USB, maybe you can connect the drive to another computer (for example via a USB to IDE & SATA adapter or a box for an external drive). And then edit the home partition.

Or you can flash an update of the BIOS to allow booting from USB.

---

