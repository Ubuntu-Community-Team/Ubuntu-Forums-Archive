---
title: "is there a way to repartition my system without reinstalling kubuntu?"
date: 2006-10-10
forum: General Help
---

### Post by maddbaron on 2006-10-10
I'd like to remove my windows xp part and redo my current kubuntu partition to incorporate the free space i get from removing xp without having to reinstall everything again.

is that possible?

---

### Post by az on 2006-10-10
> **maddbaron said:**
> I'd like to remove my windows xp part and redo my current kubuntu partition to incorporate the free space i get from removing xp without having to reinstall everything again.

is that possible?

Yes it is.  You would have to delete the partition, move or copy your Ubuntu partition there, and then edit your grub menu.list, reinstall grub and edit your fstab to reflect the new partition locations.

If your Ubuntu partition is bigger than the Windows partitions, you will have a problem.  You will not be able to copy the Ubuntu partition to that space because it would overwrite the current Ubuntu partition.  Is this the case?

---

### Post by maddbaron on 2006-10-10
nah the windows xp part is bigger by 7gig's...wow reinstall grub and edit fstab...wow....this is complicated....but the kubuntu part is smaller.

---

### Post by maddbaron on 2006-10-11
how do I do the stuff above please? i understand delete the win xp part but the editting i dont understand.

help please.

---

### Post by az on 2006-10-11
> **maddbaron said:**
> how do I do the stuff above please? i understand delete the win xp part but the editting i dont understand.

help please.

Delete the XP partition.  Move the Ubuntu partition to that free space.

Edit your grub config (/boot/grub/menu.lst) and change the (hd0,1) to (hd0,0)(as appropriate). Make it point to your changed partition.

You will need to chroot into your new partition and reinstall grub so that it known were to look for the stage 1.5 and stage 2 binaries

sudo grub-install /dev/hda

also edit fstab to make your mount points correct

sudo nano /etc/fstab

change hda2 to hda1 for example.  Do this for your / partition and your swap.  Both may have changed partition number.

That should be it, I guess.  If you can't boot into your ubuntu install, you probably made a mistake.  Boot the live cd again and make sure you have the right partitions in your menu.list and fstab.

---

### Post by handy on 2006-10-11
This might be a good solution for you too, it worked beautifuly for me... :)

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

