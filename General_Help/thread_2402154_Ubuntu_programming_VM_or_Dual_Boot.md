---
title: "Ubuntu programming VM or Dual Boot?"
date: 2018-09-26
forum: General Help
---

### Post by doom1993 on 2018-09-26
I want to use Ubuntu to learn C programming. My main machine is a Dell Inspiron 5680 with an Intel Core I7 8700, GTX 1060 3GB and 8GB RAM with a 128GB SSD and 1TB 7200RPM HDD. Windows 10 is installed on the SSD and the HDD is used for storage.In Ubuntu all i will do is programming and maybe some web browsing and that's it. Is it a better idea to dual boot for performance or is a VM enough for that? Ubuntu would be installed on the HDD but a part of it would still be used by Windows for storage.

---

### Post by QIII on 2018-09-26
I use VMs extensively for things various and sundry.  One of my machines has 13 VMs, all of which can be running at one time (a Threadripper and a truckload of memory can handle it).  If your machine is capable of running a VM, go that route.  A dual boot forces you to shut down and restart.  With a VM you just leave your primary OS running and start the VM when you need it.

---

### Post by doom1993 on 2018-09-26
My machine can handle 1 VM without slowing down too much(Because of RAM) but i want to know if 3-4GB of RAM in a VM is enough for C programming and almost nothing else(Because i would use windows for everything else), what if that programming involves 3D graphics though? How good is OpenGL support on VM Programs?

---

### Post by dragonfly41 on 2018-09-26
> [COLOR=#000000]Because i would use windows for everything else[/COLOR]
If you still intend to use Windows 10 are you aware that there is Ubuntu running native within Windows?

[https://docs.microsoft.com/en-us/windows/wsl/install-win10](https://docs.microsoft.com/en-us/windows/wsl/install-win10)

Just another option for experimenting.

---

### Post by QIII on 2018-09-26
Just remember that LSW is command line only.  No GUI desktop.

---

### Post by doom1993 on 2018-09-26
Yeah, i want a full linux install. Im just asking if Dual-Boot is worth it in this case including some 3D programming.

---

### Post by QIII on 2018-09-27
For 3D programming you probably want bare metal access.

Although you can do that with KVM, that's best achieved with two (or more) GPUs, since done that way one of the GPUs will be assigned to the VM.

In your case, I would dual boot.

---

### Post by yancek on 2018-09-27
If you do decide to install as a dual boot rather than VM, I would suggest that you carefully read the Ubuntu documentation at the site below for dual booting with windows 10/Ubuntu on an EFI machine.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by doom1993 on 2018-09-27
Thanks for the info, i have decided to dual-boot.

---

