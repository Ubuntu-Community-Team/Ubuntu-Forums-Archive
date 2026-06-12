---
title: "Acronis Drive Cloning"
date: 2019-03-08
forum: General Help
---

### Post by 1121eddie on 2019-03-08
Hello all.

I'm going to be cloning my HDD because I'm upgrading to a Samsung 860 EVO SSD. I have my system set up to dual boot with Windows 10 and Ubuntu 18.04. Is there anything I need to do with my Ubuntu set up like decrypt my home folder before I do the clone? Or is it just a case of cloning my HDD and it works like it does now?


Thanks all!

---

### Post by HermanAB on 2019-03-10
As far as I can remember, the main problem is that you need to fix the UUIDs in the /etc/fstab file after copying the disk.

Note that to copy a disk, you don't have to buy special software.  A Linux install disk has everything you need to make a copy.

---

### Post by nicholasarussell on 2019-03-10
true image is pretty smart, you might not have any issues, it also tends to extend the partitions for the larger drive.

let me know how it goes when m2 ssds get even cheaper I might upgrade my OS disk.

---

### Post by vidtek on 2019-03-10
Eddie-

When you first try to boot you will get an error.  You need to select advanced options and recovery from the grub2 menu.
When you get the options screen choose the activate networking option this makes the root/boot drive read/write.
Then in the terminal do a blkid to get your UUID's
Edit your fstab to reflect the new UUID's.
Reboot

That should do the trick.

Cheers, Tony

---

### Post by rbmorse on 2019-03-10
Acronis, in the clone mode, should produce target partitions with the same UUIDs and the original so you have to remember to disconnect the old drive before booting with the new.  Otherwise you have two drives where the partitions have the same UUIDs and that's a no-no. 

If you're using Acronis to do a plain file by file copy, then you have to manually fix etc/fstab as Herman and Tony mentioned.

---

