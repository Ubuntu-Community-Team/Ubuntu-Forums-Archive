---
title: "blacklisting a module"
date: 2013-03-30
forum: General Help
---

### Post by terminator14 on 2013-03-30
I'm trying to figure out how to properly blacklist a module (persistently), and the following is a bit confusing:

Let's take module "floppy" for example. From what I've gathered, the proper procedure is:

1. Create a .conf file under /etc/modprobe.d/
```
$ sudo vim /etc/modprobe.d/blacklist-floppy.conf

[INDENT]blacklist floppy[/INDENT]
```

2. Update initrd image:

```
$ sudo update-initramfs -u
```

3. Reboot

This procedure works great, but what exactly does step 2 do? I would think that it would recreate the initrd image with a slight change, telling it not to load the floppy module, which I guess implies that the initrd image is responsible for telling the kernel which modules to load - is this assumption correct? 

Without step 2, the change does not take effect, and the floppy module is still running after a reboot even though the blacklist-floppy.conf file is present. With it, if I want to unblacklist the floppy module, all I do is remove the file blacklist-floppy.conf and reboot and it takes effect - running step 2 again does not seem to be necessary to reverse the procedure. What exactly is step 2 doing?

---

### Post by tgalati4 on 2013-03-30
tgalati4@Mint14-Extensa ~ $ locate floppy.ko
/lib/modules/3.5.0-17-generic/kernel/drivers/block/floppy.ko
/lib/modules/3.5.0-23-generic/kernel/drivers/block/floppy.ko
/lib/modules/3.5.0-25-generic/kernel/drivers/block/floppy.ko
/lib/modules/3.5.0-26-generic/kernel/drivers/block/floppy.ko

If you need the floppy as part of the boot process (many years ago you did!), then it will get loaded into the initial ram disk file system (initramfs).  By blacklisting it, it will not get loaded into the bootstrap process, but if you have a floppy controller on your motherboard, then the kernel may load it anyway.

I don't have a floppy on this laptop, so in 12.10 I don't see the floppy module loaded:

tgalati4@Mint14-Extensa ~ $ lsmod | grep floppy

But on a desktop with a floppy header connection, you might.  You can turn the floppy off in BIOS and then the floppy module will probably not get loaded.  To prove it, take an *lsmod* snapshot of a normal boot and print it out.  Then go into BIOS and turn off your parallel port, serial port, floppy, and anything you don't need.  Then boot again and run *lsmod* and compare the two lists.  You save a little RAM and maybe a few interrupts.  Important for real-time applications, audio/video editing, etc.

I think just listing a module in one of the many blacklist configuration files is enough to keep it from being loaded by the kernel.  If you need to blacklist a module from the bootstrap/initial kernel then you would run the *update-initramfs* command.  And this would only be needed if you can't boot any linux Live CD/DVD.  It's mainly a work-around for unsupported or difficult hardware.

Also, I'm not sure if you need to create a *blacklist-floppy.conf* file, because I'm not sure if each file gets read in* /etc/modprobe.d*.  So put *blacklist floppy* in one of the other conf files.

Understand that the module loading and blacklisting framework (and hardware detection in general) has undergone many changes over the years.  So my information may be out of date and completely wrong.

---

### Post by terminator14 on 2013-04-01
> **tgalati4 said:**
> I think just listing a module in one of the many blacklist configuration files is enough to keep it from being loaded by the kernel.  If you need to blacklist a module from the bootstrap/initial kernel then you would run the *update-initramfs* command.  And this would only be needed if you can't boot any linux Live CD/DVD.  It's mainly a work-around for unsupported or difficult hardware.

So if I understand correctly, there are two types of modules - regular ones loaded by the kernel, and ones that are actually in the initramfs - and the update-initramfs only effects the initramfs ones?

---

