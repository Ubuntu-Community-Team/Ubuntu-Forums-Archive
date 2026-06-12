---
title: "why has Lubuntu got so large?"
date: 2018-06-22
forum: General Help
---

### Post by mringer on 2018-06-22
When Lubuntu first appeared it was a lightweight system intended for use on old hardware.
But in 18.04 the system requirements are:

    Memory (RAM): Your computer needs at minimum 1 GB of RAM to use Lubuntu, but we 
    recommend 2 GB or more for better performance (with web-based applications).
    Processor (CPU): You should have (at minimum) a Pentium 4, Pentium M, or AMD K8 CPU.1

(copied from [ here]("https://lubuntu.me/bionic-released") ) 

By comparison: regular Ubuntu:

Install Type....... RAM (minimum)....... RAM (recommended)....... Hard Drive
No desktop....... 128 megabytes........ 512 megabytes................ 2 gigabytes
With Desktop.... 256 megabytes........ 1 gigabyte....................... 10 gigabytes

(copied from [ here ]("https://help.ubuntu.com/lts/installation-guide/i386/ch03s04.html") )
Sorry about the dots, but I couldnt get the table to format with spaces

And for Windows 10:

Processor:................ 1 gigahertz (GHz) or faster processor or SoC
RAM:........................ 1 gigabyte (GB) for 32-bit or 2 GB for 64-bit
Hard disk space:........ 16 GB for 32-bit OS 20 GB for 64-bit OS
Graphics card:........... DirectX 9 or later with WDDM 1.0 driver
Display:.................... 800x600 

(copied from [ here ]("https://www.microsoft.com/en-gb/windows/windows-10-specifications#primaryR2") )

So: if you want a lightweight system intended for use on old hardware, what should you do?

---

### Post by Yellow Pasque on 2018-06-22
It's not necessarily that the lxde desktop is more resource hungry. The underlying components and apps in general are probably more resource hungry. A 64-bit system will use more RAM as well.

---

### Post by Holger_Gehrke on 2018-06-22
The numbers you're quoting are kind of ... misleading ...

The numbers for Ubuntu are for the lightest possible configuration you can set up when starting from a very minimal system and only adding the lightest possible programs. The numbers for LUbuntu on the other hand are for the default install. I don't have any useful numbers for a Ubuntu with the default desktop setup, but I think they'd be ever so slightly higher ...

I do have an old laptop from the early 2000s (Clevo D470W, Pentium 4 @ 3.06 GHz, 1GB Ram, 250 GB HD, ATI Radeon Mobile) which has very few problems running LUbuntu 16.04. Haven't yet tried to update it to 18.04, but I don't expect all that much trouble. On the other hand there are even lighter systems like tinycorelinux, which manages to have a working desktop in a 16mb ISO which I've had running from a 32MB DOM on an old Wyse thin client ...

Holger

---

### Post by mörgæs on 2018-06-22
It's hard to set a firm limit for how strong the hardware has to be because people's expectations and patience is different. Besides, I consider the graphics processor more important than the CPU.

What worries me a bit is that the present Lubuntu 'government' seems less determined to stay light than before. Hoping that the switch to Qt does not pull in additional fat.

---

