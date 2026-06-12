---
title: "Installing Ubuntu on Windows XP to recover data from Windows 10 hard drive"
date: 2021-06-24
forum: General Help
---

### Post by veganist on 2021-06-24
Hello everyone,

I have a HP Pavilion DV8380US laptop with XP installed. The hard drive on my Windows 10 Desktop is damaged and I want to try recovering the files. The XP laptop is the only computer I have and all the better recovery software are not compatible with XP.  Is it possible to install Ubuntu on my XP then use a Ubuntu compatible recovery software (hopefully someone here will help me find a good one), to recover the files from the Windows 10 hard drive? If this is possible, how do I go about doing this.

Here are the specifications of my HP laptop:

**Model **#: DV8380US

**Product** #: EZ698UA#ABA

**Operating system**: Windows Media Center

**Microprocessor**: 1.83 GHz
Intel Core Duo processor T2400

**Microprocessor cache**: 2MB L2 Cache

**Memory:** 2048 MB 667 MHz
DDR2 System memory (2 Dimm)

**Memory max:** 2048 MB

**Video Graphics:** NVDIA GeForce

**Video memory**: 128MB discreet
128MB shared

**Hard Drive**: 240GB 5400 RPM
Dual HDD (120 GBx2)
[B]
Display[/B]: 17.0" WXGA

**Sound**: Altec Lansing

Thanks

Errol

---

### Post by Autodave on 2021-06-24
An easy thing to try is to make a bootable USB or DVD and boot to it.  From that you will hopefully be able to access your HD and see what files are there.  You should be able to then copy them to another media.

---

### Post by CatKiller on 2021-06-24
> **veganist said:**
> The hard drive on my Windows 10 Desktop is damaged and I want to try recovering the files.

The Ubuntu install image is a fully functional Linux environment which will be able to read your data as much as the hardware's failings will allow. There are also specific data recovery live USBs if you'd prefer one of those.

---

### Post by kaori-hideki on 2021-06-25
I agree with the posters above that you should run the live USB. For 2GB RAM, I don't recommend installing Ubuntu GNOME on your hard disk. Go for Xubuntu or Lubuntu if you want to install it on a hard disk. From my experience, my computer is beeping when using Ubuntu GNOME on 4GB RAM.

---

### Post by mikewhatever on 2021-06-25
There is no way to "Installing Ubuntu on Windows XP", because Ubuntu is not a program for  Windows XP. Also, if the HDD is "damaged", no recovery program is going to help.

---

### Post by dragonfly41 on 2021-06-25
I do have an old Win XP laptop gathering dust and I considered how I might approach your task.

I would start by installing Rufus 32 bit on Win XP.

[https://allxpsoft.com/rufus-windows-xp/](https://allxpsoft.com/rufus-windows-xp/)

This can be used to create a Ubuntu LiveUSB.

You will need a USB flash drive - about 8 GB or more.

But you might not need this.  Ubuntu might be a red herring. I would install **TestDisk** for Win XP.

[https://allxpsoft.com/testdisk-windows-xp/](https://allxpsoft.com/testdisk-windows-xp/)

Next I would ensure that I have an external disk larger in size than your failing drive and this can be used to copy contents of your failing drive before it suddenly fails.

You will then be working on the cloned drive to recover your data rather than the failing drive (which might go at any moment).

I assume that your main PC cannot boot up.

So to conclude, start by running TestDisk on your Win XP laptop, but your failed drive must be removed and placed in a HDD container for Win XP / TestDisk to see it.

I use StarTech docking bay (with its own power supply)  for this purpose and indeed my Ubuntu runs on an SSD in StarTech

---

### Post by ActionParsnip on 2021-06-25
Additional: time to review your backup regime

---

### Post by yancek on 2021-06-25
If your hard drive on the windows 10 machine is damaged, why would you want to install Ubuntu on the XP laptop?  You would need to connect the hard drive from the windows 10 machine to the XP laptop to do anything.  What exactly is the problem with the windows 10 drive?  Do you get error warning on boot or is it something else?

Just use the xp machine to download an Ubuntu iso and write it to a USB and boot it on the windows 10 machine.  Or you can try using testdisk which is created for this purpose.  If you type testdisk in a search engine, you should see the site which also has stept by step instructions on its use.

    [https://www.cgsecurity.org/wiki/TestDisk_Download](https://www.cgsecurity.org/wiki/TestDisk_Download)

---

