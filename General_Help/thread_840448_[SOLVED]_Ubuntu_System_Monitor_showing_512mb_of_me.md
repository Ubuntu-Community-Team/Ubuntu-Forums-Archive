---
title: "[SOLVED] Ubuntu System Monitor showing 512mb of memory when I have 1GB"
date: 2008-06-25
forum: General Help
---

### Post by bridgeStreet on 2008-06-25
I updated my ubuntu 7.10 with the update manager. Then restarted my computer and the BIOS and Ubuntu now showing that I have 503.8MB of memory. Before the update both the BIOS and Ubuntu were showing that I had 1GB of memory. Any help please?

uname -a
Linux bridge-desktop 2.6.22-15-generic #1 SMP Tue Jun 10 09:21:34 UTC 2008 i686 GNU/Linux

CPU is a single core 32-bit: AMD Athlon XP 2800+

thanks

---

### Post by plucky on 2008-06-25
> Then restarted my computer and the BIOS and Ubuntu now showing that I have 503.8MB of memory.


If the BIOS is showing 503.8MB,then this has nothing to do with the operating system,possibly one of your memory modules is faulty.


What is your hardware? Is it a desktop or laptop?

Maybe the module needs re-seating in its slot.You can use the Memtest+ option in the Grub Menu to test your Memory after you have reseated the modules.

If it still doesn't show up,you can pull them one at a time to find which is faulty.


Good Luck

---

### Post by bridgeStreet on 2008-06-25
My CPU has single core, but as you can see with this command:
Linux bridge-desktop 2.6.22-15-generic #1 SMP Tue Jun 10 09:21:34 UTC 2008 i686 GNU/Linux

The new kernel that came with the update I did, has SMP (Symmetric multiprocessing) enabled. Therefore it thinks I have two core processor and half's the memory for each core.

How do I tell the kernel to disable SMP.

Everything was okay, before the update.

Thanks

---

### Post by bridgeStreet on 2008-06-25
> **plucky said:**
> What is your hardware? Is it a desktop or laptop?

I am using a desktop

Thanks

---

### Post by VMC on 2008-06-25
From inside a Terminal, execute this command. It will show you not only how much memory but also the type of dram:

```
 sudo lshw -short
```

---

### Post by bridgeStreet on 2008-06-25
H/W path            Device     Class          Description
=========================================================
                               system         KT400A-8237
/0                             bus            KT400A-8237
/0/0                           memory         128KB BIOS
/0/5                           processor      AMD Athlon(tm) XP 2800+
/0/5/a                         memory         128KB L1 cache
/0/5/b                         memory         512KB L2 cache
/0/1c                          memory         512MB System Memory
/0/1c/0                        memory         DIMM [empty]
/0/1c/1                        memory         512MB DIMM
/0/1c/2                        memory         DIMM [empty]
/0/100                         bridge         VT8377 [KT400/KT600 AGP] Host Brid
/0/100/1                       bridge         VT8235 PCI Bridge
/0/100/1/0                     display        NV18 [GeForce4 MX 4000]
/0/100/a                       communication  536EP Data Fax Modem
/0/100/f                       storage        VIA VT6420 SATA RAID Controller
/0/100/f.1                     storage        VT82C586A/B/VT82C686/A/B/VT823x/A/
/0/100/f.1/0        ide0       bus            IDE Channel 0
/0/100/f.1/0/0      /dev/hda   disk           76GB Maxtor 6Y080L0
/0/100/f.1/0/0/1    /dev/hda1  volume         74GB Linux filesystem partition
/0/100/f.1/0/0/2    /dev/hda2  volume         1466MB Extended partition
/0/100/f.1/0/0/2/5  /dev/hda5  volume         1466MB Linux swap / Solaris partit
/0/100/f.1/0/1      /dev/hdb   disk           SAMSUNG DVD-ROM SD-616Q
/0/100/f.1/1        ide1       bus            IDE Channel 1
/0/100/f.1/1/0      /dev/hdc   disk           SAMSUNG CD-R/RW DRIVE SW-252F
/0/100/10                      bus            VT82xxxxx UHCI USB 1.1 Controller
/0/100/10.1                    bus            VT82xxxxx UHCI USB 1.1 Controller
/0/100/10.2                    bus            VT82xxxxx UHCI USB 1.1 Controller
/0/100/10.3                    bus            VT82xxxxx UHCI USB 1.1 Controller
/0/100/10.4                    bus            USB 2.0
/0/100/11                      bridge         VT8237 ISA bridge [KT600/K8T800/K8
/0/100/11.5                    multimedia     VT8233/A/8235/8237 AC97 Audio Cont
/0/100/12           eth0       network        VT6102 [Rhine-II]

---

### Post by plucky on 2008-06-26
> /0/1c memory 512MB System Memory
/0/1c/0 memory DIMM [empty]
/0/1c/1 memory 512MB DIMM
/0/1c/2 memory DIMM [empty]


I think you have lost a memory module.Of your three slots,two are empty.

---

### Post by bridgeStreet on 2008-06-26
> **plucky said:**
> I think you have lost a memory module.Of your three slots,two are empty.

If I look inside my computer I can see two memory modules.

Thanks

---

### Post by plucky on 2008-06-26
> If I look inside my computer I can see two memory modules.


You find out which one is not working,just remove one at a time.If you remove one and can still see 512M,then that is the broken one.

By the look of things it is not the one in the middle slot.

Please unplug your computer and leave unplugged for a while to let any charge drain away before removing memory modules.Also take anti-static precautions,so that you don't damage any electronics.


Good Luck

---

### Post by bridgeStreet on 2008-06-26
Just ran memtest86+ changed it to probe the memory map. Then booted into Ubuntu and got 1GB of memory showing in System Monitor.

Very strange??

When I ran memtest86+ with defaults it didn't help.

Thanks

---

### Post by bridgeStreet on 2008-06-26
sudo lshw -short

H/W path            Device     Class          Description
=========================================================
                               system         KT400A-8237
/0                             bus            KT400A-8237
/0/0                           memory         128KB BIOS
/0/5                           processor      AMD Athlon(tm) XP 2800+
/0/5/a                         memory         128KB L1 cache
/0/5/b                         memory         512KB L2 cache
/0/1c                          memory         1GB System Memory
/0/1c/0                        memory         512MB DIMM
/0/1c/1                        memory         512MB DIMM
/0/1c/2                        memory         DIMM [empty]
/0/100                         bridge         VT8377 [KT400/KT600 AGP] Host Brid
/0/100/1                       bridge         VT8235 PCI Bridge
/0/100/1/0                     display        NV18 [GeForce4 MX 4000]
/0/100/a                       communication  536EP Data Fax Modem
/0/100/f                       storage        VIA VT6420 SATA RAID Controller
/0/100/f.1                     storage        VT82C586A/B/VT82C686/A/B/VT823x/A/
/0/100/f.1/0        ide0       bus            IDE Channel 0
/0/100/f.1/0/0      /dev/hda   disk           76GB Maxtor 6Y080L0
/0/100/f.1/0/0/1    /dev/hda1  volume         74GB Linux filesystem partition
/0/100/f.1/0/0/2    /dev/hda2  volume         1466MB Extended partition
/0/100/f.1/0/0/2/5  /dev/hda5  volume         1466MB Linux swap / Solaris partit
/0/100/f.1/0/1      /dev/hdb   disk           SAMSUNG DVD-ROM SD-616Q
/0/100/f.1/1        ide1       bus            IDE Channel 1
/0/100/f.1/1/0      /dev/hdc   disk           SAMSUNG CD-R/RW DRIVE SW-252F
/0/100/10                      bus            VT82xxxxx UHCI USB 1.1 Controller
/0/100/10.1                    bus            VT82xxxxx UHCI USB 1.1 Controller
/0/100/10.2                    bus            VT82xxxxx UHCI USB 1.1 Controller
/0/100/10.3                    bus            VT82xxxxx UHCI USB 1.1 Controller
/0/100/10.4                    bus            USB 2.0
/0/100/11                      bridge         VT8237 ISA bridge [KT600/K8T800/K8
/0/100/11.5                    multimedia     VT8233/A/8235/8237 AC97 Audio Cont
/0/100/12           eth0       network        VT6102 [Rhine-II]

Everything looks okay now

Thanks

---

### Post by VMC on 2008-06-26
If your satisfied then please mark this topic solved.

I would do as suggested. Find that one module that was not showing up and re-seat it. It may come back to haunt you again. 

It's not rocket science. Just power down the pc and wait a few minutes. Make sure it's unplugged and then pull the dimm out and check its contacts.

 I use a pencil eraser to clean my contacts. But just removing and reinstalling should work.

---

