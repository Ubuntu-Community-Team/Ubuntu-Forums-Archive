---
title: "nvidia drivers for hardy"
date: 2008-04-28
forum: General Help
---

### Post by upthelum on 2008-04-28
Has anyone seen this error from wine before. I'm trying to install nvidia 7600 GS driver but envy doesn't like it.

Please help i need desktop effects enabled.

---

### Post by ryanhaigh on 2008-04-28
Can you post the output of lspci? Have you tried using the standard nvidia-glx-new driver from the repos?

---

### Post by upthelum on 2008-04-28
I'll give that a try.

---

### Post by ryanhaigh on 2008-04-28
The output of lspci seems to indicate that you are running ubuntu in a vmware session is that correct?

---

### Post by upthelum on 2008-04-28
Yes. It has not been a problem before though. Just getting to known Hardy before i do an upgrade on my laptop.

---

### Post by ryanhaigh on 2008-04-28
You cannot use the nvidia drivers in vmware, even if you could install them they are not the right drivers for the virtual display device and so they would not work. You also cannot run compiz (desktop effects) in a vmware session. 

That said if you really want to try it I suggest installing nvidia-glx or nvidia-glx-new as they probably don't do the hardware check that envy is obviously performing. 

Post back if you somehow get it to work.

---

### Post by upthelum on 2008-04-28
Ok thanks i will.

---

### Post by jespdj on 2008-04-28
When you run Ubuntu in a virtual machine, for example in VMWare or VirtualBox, then it will see virtual hardware - not the real hardware that's in your computer.

So it won't see that you have an nVidia graphics card in your computer - instead it will see a virtual video card that VMWare or VirtualBox emulates.

Installing the nVidia driver will not work. It will not give you accelerated 3D graphics in your virtualized OS. Even if you can install the driver, then it will not work properly.

---

### Post by upthelum on 2008-04-29
> **jespdj said:**
> When you run Ubuntu in a virtual machine, for example in VMWare or VirtualBox, then it will see virtual hardware - not the real hardware that's in your computer.

So it won't see that you have an nVidia graphics card in your computer - instead it will see a virtual video card that VMWare or VirtualBox emulates.

Installing the nVidia driver will not work. It will not give you accelerated 3D graphics in your virtualized OS. Even if you can install the driver, then it will not work properly.

Nice one thanks...

---

