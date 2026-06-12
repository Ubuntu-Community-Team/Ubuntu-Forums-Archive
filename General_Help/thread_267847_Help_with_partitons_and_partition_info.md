---
title: "Help with partitons and partition info"
date: 2006-09-29
forum: General Help
---

### Post by Daniel15 on 2006-09-29
Hi everyone,
 Recently, I decided to try out Microsoft's new Windows Vista RC1 (it's horrible, by the way :P). To do so, I resized my Windows partition, and inserted a new partition from the new free space. 

Here's what I did:

**Old partition layout:**
*Primary partitions:*
/dev/sda1 - Dell recovery partition
/dev/sda2 - Windows XP Home
/dev/sda3 - Another Dell partition (at END of disk)

*Logical partitions:*
/dev/sda5 - Linux root (/)
/dev/sda6 - Linux /home
/dev/sda7 - Swap

----------
**New partition layout:**
*Primary partitions:*
/dev/sda1 - Dell recovery partition
/dev/sda2 - Windows XP Home
/dev/sda3 - Another Dell partition (at END of disk)

*Logical partitions:*
_/dev/sda5 - Windows Vista_
/dev/sda6 - Linux root (/)
/dev/sda7 - Linux /home
/dev/sda8 - Swap

As you can see, since I added the Windows Vista partition from the free space created by resizing the Windows XP partition, all my Linux partitions moved up a bit. I've edited /etc/fstab to refer to the new partitions, and changed /boot/grub/menu.lst to refer to the correct root partition, however I'm still having a problem: Whenever I run update-grub (eg. a new kernel is installed), it overwrites my changed /boot/grub/menu.lst entries with the old ones (all mentioning /dev/sda5). My question is, where is this stored? And how can I change it to /dev/sda6?

I was also having a problem with hibernating, but I think I've solved that now (by editing /etc/mkinitramfs/conf.d/resume, and also editing /boot/grub/menu.lst, adding the 'resume=' option.

If anyone could help me by telling me what else I have to change, it would be appreciated :)

--Daniel15

EDIT: Indeed, hibernation is working perfectly again :D

---

