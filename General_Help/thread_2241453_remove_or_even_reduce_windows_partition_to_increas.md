---
title: "remove or even reduce windows partition to increase ext4"
date: 2014-08-26
forum: General Help
---

### Post by john281 on 2014-08-26
Hi there,

I would like some help. The best thing for me would be to safely remove both NTFS partitions and use that unallocated space to extend ext4. 
I have already made a backup and also have the live USB stick to boot and use Gparted.
Howver if you see from the image my ext4 (sda5) is within extended (sda3). What would be the best way to merge that unallocated space to ext4 without messing up the swap and the successful boot.

Thanks

---

### Post by grahammechanical on 2014-08-26
The sda5 is a logical partition inside an extended partition (sda3). Machines like yours and mine have a 4 primary partition limit. To get around that we use one of the 4 permitted primary partitions to be an Extended partition. Then we can create as many Logical partitions inside the Extended partition. 

When Ubuntu was installed it created a primary partition and turned it into an Extended partition (sda3). Then the installer created 2 Logical partitions inside the Extended partition (sda5 and swap). You need to resize the Extended partition (sda3) first and then resize sda5 afterwards. 

Regards.

---

### Post by john281 on 2014-08-26
So first resize the Extended and increase by the unalocated space and then once inside the extended, resize the ext4. I tried this but it created a smaller unnalocate part in the right hand side. Anyway thanks

---

### Post by ajgreeny on 2014-08-26
I can not work out why a small unallocated space was made at the right hand end of the extended partition unless you moved the sda5 instead of enlarging it by grabbing the left hand end and moving it to the left as far as possible.

Without actually carrying out the changes can you show another screenshot of the problem you have seen; just queue all the changes as you have done so far and come back again with the pic.  Don't worry about your swap; we can manage that as needed after any changes have been made, and in fact 8GB swap is quite a large one, so unless you need to hibernate the system which has the same amount of ram, you could probably easily manage with less swap.

When enlarging a partition be prepared to wait for a long time whilst the edit is actually carried out and do not cancel once started or you will be in big trouble. Also make sure that a laptop is plugged in to a mains electricity supply to ensure it does not shutdown while in action.

---

