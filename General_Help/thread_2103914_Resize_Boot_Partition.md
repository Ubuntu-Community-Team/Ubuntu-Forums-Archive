---
title: "Resize Boot Partition"
date: 2013-01-11
forum: General Help
---

### Post by afsfire on 2013-01-11
When I boot my Ubuntu 12.04 LTS Server (which is a vSphere Virtual Machine) I get an error saying that the there is 0 space in the boot partition. I have archived a lot of old Kernel files off of that partition however it still says that there is 0 space. I would like to increase the size of the boot partition but am having trouble finding any instructions on how to do this. I have increased the disk space to the VM and booted to gparted Live but it will not let me resize the boot partition. This is my first Linux server so I am still very green. Any Ideas?

---

### Post by dino99 on 2013-01-11
gparted (and all the other partitioning tools) works on real hardware, not on virtual (seems logical dont you ?)

Look at the VM settings to do changes

---

### Post by afsfire on 2013-01-11
Thanks, but the vm settings will allow me to add the disk space. However it is not going to allow me to change the size of a partition. Whether it be Windows or Ubuntu.

---

