---
title: "Boot up problems"
date: 2008-02-22
forum: General Help
---

### Post by lucasp on 2008-02-22
Hi im a complete newbie to linux so bear with me, i have just installed 7.10 and the boot up is incredibly slow, i was having trouble with an mpbios timer  so i disabled apic but the boot still takes upwards of 3 minutes. i have i dsg re branded ecs 331( im ashamed i know now) bootchart attached

---

### Post by philinux on 2008-02-22
Click the link below for known bugs. Slow boot up is one of them.

---

### Post by lucasp on 2008-02-22
im sure its something more than just a bug is there anyway i can log the messages in boot up

---

### Post by dstew on 2008-02-22
It looks like the processes s10udev and udevsettle are responsible. These are part of the udev system, which is part of the hotplug system. They are services that are responsible for reacting to plugging or unplugging USB devices, among other things.

Your boot might slow at this point because you have USB devices plugged in. Maybe your BIOS has different USB modes that are interfering with the initialization of udev. So, try booting without USB devices plugged in, to see if it is faster. Also, look at your BIOS settings that have to do with USB devices. Sometimes, it helps to disable the BIOS routines that detect USB devices. Also, you should try disabling Legacy USB support in the BIOS if it is there.

---

### Post by philinux on 2008-02-22
> **lucasp said:**
> im sure its something more than just a bug is there anyway i can log the messages in boot up

Yes. /var/log/messages

---

### Post by lucasp on 2008-02-24
sorry for late reply (waiting for it to boot up :) ) i dont have any devices connected to my laptop, so i dont think its that ive attatched the latest message logs i didnt know where to start with them

---

### Post by lucasp on 2008-02-25
i really dont like doing this but 
BUMP!

---

### Post by dstew on 2008-02-25
It seems the slowdown is coming from the interrupts from your CD-ROM drive. Try removing the **noapic** from your kernel line in /boot/grub/menu.lst. This will enable the advanced programmable interrupt controller. You may have put that on the kernel line during installation, but once installed, it is probably no longer needed.

---

