---
title: "Resizing Virtual Machine Disk"
date: 2007-06-03
forum: General Help
---

### Post by Jamie Jackson on 2007-06-03
I made an XP VM too small, so I'm trying to resize it. I've read that it's not possible to resize the virtual disk, and saw a recommendation to create a new disk in the VM, and clone the small disk's contents to the new disk.

So, I did that, and I cloned the 2GB vmdk to the 4GB vmdk using partimage.

However, if I remove the small disk from the VM, the VM won't boot. It runs through its BIOS memory check, then it goes to a blank black screen.

Any idea where I went wrong?

I could have just reinstalled XP on a bigger VM, and not have blown the weekend trying to resize the existing one, but I have a hard time accepting defeat. ;-)

Thanks,
Jamie

---

### Post by Jamie Jackson on 2007-06-21
I'm trying this again. I think the last time I didn't restore the MBR from the original to the new disk.

However, using System Rescue CD's partimage, when I try to restore the MBR, I get:

Can't read block 0 from image (59)

What's that all about!!

Details:
I'm dealing with NTFS partitions.
I ripped the image using no compression, and split the image in ~2GB chunks (leaving me with 2 chunks)

Thanks,
Jamie

---

