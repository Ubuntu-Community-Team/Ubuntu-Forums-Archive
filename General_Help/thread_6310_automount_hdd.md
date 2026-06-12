---
title: "automount hdd"
date: 2004-11-27
forum: General Help
---

### Post by tanari on 2004-11-27
Why additionals hdds don't automount like they do in windows?
I must run sudo mount -t ntfs /dev/hdb /mnt/ntfs  :(.
It is not user friendly. How can I mount digital camera or other usb devices, if I will buy them?

---

### Post by wazoo42 on 2004-11-27
If you put additional lines in the /etc/fstab file they will mount on startup.

---

### Post by calvinpriest on 2004-11-27
Windows partitions are not automatically mounted by the Ubuntu installer, but hopefully this will be changed in the next version (Hoary). 

As the previous poster said, you will have to add additional lines to the /etc/fstab file.   1) Create a directory called /mnt/windows (or similar).
2) Assuming the Windows partition is on hda1, add the following line to /etc/fstab: /dev/hda1 /mnt/windows ntfs defaults,ro 0 0

These changes will be read on re-boot and the partition should be automatically mounted.  If you aren't sure of the partition name, you can view graphically from Applications->System Tools->System Monitor (Resource Monitor tab, at bottom).

USB devices, however, should mount automatically, and a nautilus window should open.  My digital camera and usb pen drive both work this way.

---

