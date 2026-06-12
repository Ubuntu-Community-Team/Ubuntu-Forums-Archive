---
title: "How can i convert a virtual box vdi and install it on an actual hard drive partition?"
date: 2015-12-20
forum: General Help
---

### Post by jj4 on 2015-12-20
I plan to run this to create an image VBoxManage internalcommands converttoraw your-virtualbox-disk.vdi /dev/sdX

I have an employ partition ready but I also already have 1 Linux partition and 2 windows partitions losing from a grub boot loader. This IMG would be the 4th partition (also windows). How can I get it to boot properly?

---

### Post by SeijiSensei on 2015-12-20
Usually running "sudo grub-update" is sufficient.

---

