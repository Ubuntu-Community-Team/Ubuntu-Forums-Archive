---
title: "Is your bootable  flag up?"
date: 2008-01-22
forum: General Help
---

### Post by ele_mugv on 2008-01-22
Hi,

Pls help :confused: What is a bootable flag? What does it mean when it's on, what does it mean when it's off?

Ur response is critical.

Thanks,
Ele

---

### Post by forestpixie on 2008-01-22
when it's on the partition is bootable and when it's off it's not

Edit - next post has a bit more detail :)

---

### Post by plucky on 2008-01-22
> when it's on the partition is bootable and when it's off it's not

I don't think that is quite right. On a multi distro system there is only one partition that has a boot flag on it. This is where grub goes to look for the menu.lst file to boot each distro.

That partition has the boot flag set.

Menu.lst then loads the selected kernel from its own boot partition.

If I am wrong can someone more Knowledgable correct me!

---

