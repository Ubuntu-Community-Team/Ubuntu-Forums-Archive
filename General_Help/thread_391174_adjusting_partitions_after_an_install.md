---
title: "adjusting partitions after an install"
date: 2007-03-22
forum: General Help
---

### Post by adriant51 on 2007-03-22
Hi, I just installed Kubuntu and I have to say I'm very impressed. I've been a debian user since 1998 and if I can just get a few things figured out I think I'll be a permanent convert.

I would like to remove a partition and grow an existing partition. I know how to use parted so that's not the problem. I'd like to know what I need to do afterwards. In the past I would edit /etc/lilo.conf and /etc/fstab then rerun lilo and all would be well. I'm not sure what I should be editing/running after modifying my partitions. It seems like the important files are auto-generated.

Thanks,
 Adrian

---

### Post by Kateikyoushi on 2007-03-22
It depends on which partitions you want to delete and resize, you might have to yse a live disc for that.
What you have to edit is /boot/grub/menu.lst (this depends on which partitions you change and might not be necessary) and the fstab.

---

### Post by zvacet on 2007-03-23
Do it with Gparted Live CD.I tryed it yesterday for a first time and it was like snaping a fingers.

---

