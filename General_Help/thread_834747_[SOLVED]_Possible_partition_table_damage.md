---
title: "[SOLVED] Possible partition table damage"
date: 2008-06-19
forum: General Help
---

### Post by init1 on 2008-06-19
I was using a hard drive partitioner and I think I've messed up my partition table. Gparted shows my hard drive as one unallocated space, but fdisk seems to report what I expect. I'm afraid that if I reboot I won't be able to get back into my system. How can I tell if I've messed things up, and if so, how can I fix it?  I have used TestDisk before, and I was able to recover all my data, but I had to reinstall Ubuntu because the system wasn't booting correctly anymore.

---

### Post by logos34 on 2008-06-20
> **init1 said:**
> parted shows my hard drive as one unallocated space, but fdisk seems to report what I expect.

I get this a lot.

If it's just the partition table, then TestDisk should be able to fix it. 

What partitioning tool were you using before it screwed things up?

---

### Post by cod3rbro on 2008-06-20
Save your data, format your entire drive.

---

### Post by init1 on 2008-06-21
> **logos34 said:**
> I get this a lot.

If it's just the partition table, then TestDisk should be able to fix it. 

What partitioning tool were you using before it screwed things up?
After I rebooted, I was able to get into Debian fine, but Ubuntu appeared to be lost. I decided to try Testdisk today and although its not exactly as it was before, I've got all the data I wanted back. 
I was using XFDISK (a DOS partition tool) inside QEMU (a PC emulator) to try to install FreeDOS without rebooting.

---

### Post by logos34 on 2008-06-21
> **init1 said:**
>  I was using XFDISK (a DOS partition tool) inside QEMU (a PC emulator) to try to install FreeDOS without rebooting.

ok, I see.

Well, at least it wasn't a total wash--got your data back at least even if testdisk didn't completely fix things.

Enjoy!

---

