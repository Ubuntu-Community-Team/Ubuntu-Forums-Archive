---
title: "Resizing Clonezilla restoration with GParted (potential boots issues?)"
date: 2015-11-14
forum: General Help
---

### Post by LastHylian on 2015-11-14
[IMG]http://i.imgur.com/sQYGKU0.png[/IMG]

This is a Clonezilla restoration to a bigger SSD than the original. I can resize the partitions the way I want, but GParted warns me about the disk potentially not being able to boot afterwards and that GParted can fix this. What is it referring to and how would I fix it in that situation? The resizing has to be done in a weird order too since the swap is right in the middle. From what I've played with, I would need to expand swap to the end, then pull it up to make it smaller again, then finally, expand the ext4 partition to full.

Thanks guys.

---

### Post by mikewhatever on 2015-11-14
It should boot ok, but you need to move swap and the extended partition to the end, rather then expand it. Also, comment swap out in /etc/fstab for now. The UUID is probably going to change, so you'll need to edit it later.

---

### Post by egeezer on 2015-11-14
A crude but effective way would be to delete the swap partition, create a new one at the end of the unallocated partition, then just expand sda1 to the size you want.

Swap doesn't contain any files to lose, and the new UUID will be created automatically

---

