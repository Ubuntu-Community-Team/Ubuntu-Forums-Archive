---
title: "Custom LUKS encryption"
date: 2017-09-29
forum: General Help
---

### Post by the-dreams-wind on 2017-09-29
I'm looking for a way to install Ubuntu from scratch with LUKS encryption enabled with custom Partitioning Table. 
Default configuration works quite well but i want to place home folder on a separate partition, that is not possible when installing system with default partitioning.
I also need to have swap, but i need it encrypted as well. To my surprise when making a space 'physicall volume for encryption' i cannot add under it more than one item. So i don't understand how to make swap and root / encrypted together alongside unencrypted home folder and boot.

---

### Post by TheFu on 2017-09-29
The default Ubuntu encryption uses a single partition to hold all the PVs, VGs, and LVs.  Think of LVs as highly flexible partitions.  These can be resized even on a running system if the file system is ext4.  Cloning LVs is easy too.  Since the entire partition is LUKS encrypted, it is actually difficult to make any part of the disk, outside the /boot/ partition, NOT be encrypted.  I've done it myself - it wasn't trivial.

So .... my advice is to begin with a standard installation using whole disk encryption (which encrypts everything except /boot).  It will use LVM and you can shrink an LV, then create one for /home.  Swap will already be encrypted and so will the new /home LV.  Done and done.

LVM brings a number of other advanced capabilities to the game too, but you probably should just learn enough to shrink a partition to make room for a new LV for the /home to be placed.

You will begin with something like this:
```
$ lsblk 
NAME                          MAJ:MIN RM   SIZE RO TYPE  MOUNTPOINT
sda                             8:0    0 119.2G  0 disk  
&#9500;&#9472;sda2                          8:2    0   488M  0 part  /boot
&#9500;&#9472;sda3                          8:3    0  70.8G  0 part  
&#9474; &#9492;&#9472;crypt1                    253:0    0  70.7G  0 crypt 
&#9474;   &#9500;&#9472;ubuntu--vg-root   253:1    0  57.4G  0 lvm   /
&#9474;   &#9492;&#9472;ubuntu--vg-swap_1 253:2    0   4.1G  0 lvm   [SWAP]
&#9492;&#9472;sda1                          8:1    0   512M  0 part  /boot/efi

```
Oh - I forgot that /boot/efi isn't encrypted either. Sorry.

So - sda1 and sda2 are for booting.  sda3 is completely encrypted and there is a swap and root logical volume left.  Now, I resized my encrypted partition and removed the 46G partition from the listing above that isn't encrypted.  Needed that for a travel need, which I suspect you don't have.

---

