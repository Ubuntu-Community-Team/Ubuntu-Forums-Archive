---
title: "Move Ubuntu Partition to extended (triple boot situation)"
date: 2008-04-30
forum: General Help
---

### Post by SlalomMan on 2008-04-30
I've got Windows Vista and Ubuntu 7.10/8.04 (the upgrade didn't go to completion, so I believe I have bits and pieces) on my 250GB hard drive. I want to try out OSX86 on this computer. I need to make another primary partition, so I was told to move my swap to an extended partition and then use the mac partition in there. I have read that OSX needs a primary partition; a logical partition won't work. My setup is as follows:

Some unallocated space (1MB, don't know how it got there)
dev/sda0 - ntfs - 1.46GB - Toshiba's recovery partition
dev/sda1 - ntfs - 186.43GB - Vista partition
Some unallocated space (2.49MB)
dev/sda4 - extended - 30GB - Extended partition
---dev/sda6 - fat32 - 15GB - Mac Partition (but I want to move it)
---Unallocated Space (15GB)
---dev/sda5 - 509.88MB - swap - Linux Swap
dev/sda3 - ext3 - 14.52GB - Ubuntu partition

Now, I want to, bascially, switch out the Ubuntu and mac partitions...basically delete the extended partition, make a new one that is about 15GB, put Ubuntu and the swap into that extended partition, and then use the unallocated space at the end (probably 30GB or so) for OSX86. Is there anyway I can move an existing primary partition into an extended partition, making it a logical partition?

I know I can delete the swap and recreate it inside an extended partition, but I need to move the ubuntu partition as well.

Any help would be greatly appreciated.

---

### Post by louieb on 2008-04-30
Gparted can copy partitions. The target need to be the same size or larger.
or use someting like partimage or clonezilla. Probably will have to  setup grub to reflect the move. And file /etc/fstab will need updating too.

---

### Post by SlalomMan on 2008-04-30
Alright, I'm new to the inner workings on linux. Would I need to boot from a liveCD to copy the partition? I guess I would have to unmount to do that. And I would just edit the Grub menu.lst file, right?

And of course the fstab file...I haven't really looked at that.

---

