---
title: "Moving Linux Partitions"
date: 2006-10-27
forum: General Help
---

### Post by zgornel on 2006-10-27
I have to move my Linux (ext3) and swap partitions. Will grub be able to boot from the new locations ? (grub is located in mbr)

---

### Post by Tambo on 2006-10-27
When you say move what do you mean? From hda1 to hda2 or similar? You will have to edit grub.conf to adapt to the changes, shouldn't be to much of a hassle.

---

### Post by zgornel on 2006-10-27
No no. Move both partitions towards other areas of the drive. The only things that will change will be the physical locations. The partition names won't change.

---

### Post by aysiu on 2006-10-27
You can use PartImage. You'll have to adjust the /boot/grub/menu.lst and /etc/fstab files accordingly.
[http://www.psychocats.net/ubuntu/partimage](http://www.psychocats.net/ubuntu/partimage)

---

### Post by boban on 2006-10-27
> **aysiu said:**
> You can use PartImage. You'll have to adjust the /boot/grub/menu.lst and /etc/fstab files accordingly.
[http://www.psychocats.net/ubuntu/partimage](http://www.psychocats.net/ubuntu/partimage)

I used gparted (it's in repositories) for moving partitions, but I don't remember if I had to do something with grub (I guess, that if I don't remember, then I didn't need to do anything ;) ).

---

### Post by zgornel on 2006-10-27
I'll do that and see what happens :)

---

### Post by boban on 2006-10-30
> **zgornel said:**
> I'll do that and see what happens :)

And what has happened? :)

---

### Post by zgornel on 2006-10-30
Not tried it yet, I enlarged the partition and that's about it :D .

---

