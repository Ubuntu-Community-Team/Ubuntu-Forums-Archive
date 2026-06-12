---
title: "How to resize primary partition with unallocated space"
date: 2012-12-20
forum: General Help
---

### Post by qplace on 2012-12-20
I am trying to resize a bootable primary partition using unallocated space. My ubuntu installation is running under vmware player. GParted table of the partitions look like this:

Partition    FileSystem   MountPoint  Size(GB)
/dev/sda1    ext4         /           19
unallocated  unallocated              60
/dev/sda2    extended                 1
   /dev/sda5 linux-swap               1

I don't understand how can I extend /sda1 with unallocated space using GParted (may be I should use smth else?). I'll appreciate any help in pointing me to the right steps, preferrably without using liveCD or booting from CD. 

Thank you

---

### Post by Merrattic on 2012-12-20
You won't be able to resize a running partition. So if the primary partition you want to resize has your booted up ubuntu on it you can't do it. You will have to boot from a Parted Magic CD or similar that has gparted on it in order to reallocate free space.

As you are working with a VM, you can download a partedmagic iso and simply attach it to the VM and run it.

Once gparted is up and running, select the partition you want to extend, right click on it and choose resize/move, then drag the arrows at either end to where you want them, then click on the resize/move button bottom right. This sets up the action but doesn't implement it. When ready, click on the "Apply All Operations" button on the icon menu, and wait. If all goes well, your partition should be resized.

---

### Post by dannyboy79 on 2012-12-20
i'd like to point out that you may want to back up any critical files as sometimes extending/resizing partitions can cause data loss/corruption. It's a "possibility" I am saying. Always backup "just in case"

---

