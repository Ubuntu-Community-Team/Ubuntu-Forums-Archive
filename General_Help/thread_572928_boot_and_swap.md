---
title: "/boot and swap"
date: 2007-10-11
forum: General Help
---

### Post by palintheus on 2007-10-11
When I installed I partitioned in a /boot and made a swap of 2gig, I am now thinking I do not need the /boot and rarely touch the swap, is there a way to remove the /boot and reduce the swap size?

I am willing to post any file contents needed.

---

### Post by bodhi.zazen on 2007-10-11
Well, you must move /boot to your / partition as you need a /boot somewhere ..., similar to moving home.

Swap you can test with ```
sudo swapoff
```

Just comment out the swap line in /etc/fstab

---

### Post by palintheus on 2007-10-11
ok, but since its at the beginning of my drive, how do I merge it into the /, and then do I just flag it with gparted(or similar)?

---

### Post by bodhi.zazen on 2007-10-11
You will need a newer version of gparted to merge your partition. The gparted live CD or gutsy will do ...

After you merge you will likely need to update /boot/grub/menu.lst and /etc/fstab manually. You should do this from the live CD ...

---

### Post by palintheus on 2007-10-11
hmm, this is beginning to look like i could screw something up, might tackle it this weekend.

what would need to be done to /boot/grub/menu.lst and /etc/fstab

---

### Post by bodhi.zazen on 2007-10-11
Depends ... if you mount by uuid, nothing

If you mount by /dev or (hd0,0) you have to make sure to update the various partitions if they change. Like you kernel lines in /boot/grub/menu.lst and fstab.

---

