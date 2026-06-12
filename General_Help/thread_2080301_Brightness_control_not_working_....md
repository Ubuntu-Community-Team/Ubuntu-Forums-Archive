---
title: "Brightness control not working ..."
date: 2012-11-03
forum: General Help
---

### Post by Rob Sayer on 2012-11-03
Just installed xubuntu 12.04, replacing ubuntu 12.04 ... don't like unity or gnome anymore.

Previously installed xfce 4.8 over ubuntu but seemed iffy, figured xubuntu would work better.

It does ... except I can't turn down the screen brightness anymore.  I could with xfce/ubuntu.  Neither the keys nor the panel app work.

Very frustrating ...

Acer 5742 laptop, i3 with intel integrated HD graphics.

Any suggestions?

---

### Post by Toz on 2012-11-03
Try adding the **acpi_backlight=vendor** kernel parameter. Like this:

1. Edit the grub configuration file:
```
gksu leafpad /etc/default/grub
```

2. Add the paramater to the line:
> GRUB_CMDLINE_LINUX=""
...so that it reads:
```
GRUB_CMDLINE_LINUX="acpi_backlight=vendor"
```

3. Save the file.

4. Update grub with the changes:
```
sudo update-grub
```

5. Reboot and test.

---------

If it doesn't work, post back the results of:
```
cat /proc/cmdline
```
...so we can check if its correct.

---

### Post by Rob Sayer on 2012-11-03
Worked like a charm ... the brightness plugin works fine now.

Thanks for the quick reply ...

---

### Post by floycheccp on 2013-01-28
Hi, 
I've the same problem: Xubuntu 12.10 on a Asus eeepc. When the system starts, the brightness is very low and I cannot do nothing to change it.


this is the video driver:

00:02.0 VGA compatible controller [0300]: Intel Corporation Atom  Processor D2xxx/N2xxx Integrated Graphics Controller [8086:0be1] (rev  09) (prog-if 00 [VGA controller])
    Subsystem: ASUSTeK Computer Inc. Device [1043:84a9]
    Flags: bus master, fast devsel, latency 0, IRQ 44
    Memory at dfc00000 (32-bit, non-prefetchable) [size=1M]
    I/O ports at f0e0 [size=8]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: <access denied>
    Kernel driver in use: gma500
    Kernel modules: gma500_gfx

cat /proc/cmdline:
BOOT_IMAGE=/boot/vmlinuz-3.5.0-22-generic root=UUID=e3b66131-fda6-43be-8d20-2339b08f4ef6 ro quiet splash vt.handoff=7

I did every steps of your post but nothing changed...
Thanks

---

### Post by Toz on 2013-01-28
Hello and welcome to the forums.

> cat /proc/cmdline:
BOOT_IMAGE=/boot/vmlinuz-3.5.0-22-generic root=UUID=e3b66131-fda6-43be-8d20-2339b08f4ef6 ro quiet splash vt.handoff=7


Are you sure that you ran step #4? The parameter "acpi_backlight=vendor" is not showing up in your kernel boot line.

---

### Post by Rob Sayer on 2013-01-29
> **floycheccp said:**
> Hi, 
I've the same problem: Xubuntu 12.10 on a Asus eeepc...

This is an intel atom 2600 or thereabouts cedar trail/cedar view graphics machine?  The gma500 and 3600 graphics machines are a bit of a bucket of worms with linux.  The graphics were outsourced by intel and are closed source.

If so, hate to say this, but you'll have to use 32 bit 12.04 lts ubuntu with that gpu.  Simple as that.  There are cedarview driver packages out there but they are only 32 bit and you have to use 12.04.

I have a similar acer netbook and I ended up installing mint after much frustration with xubuntu recently.  Like, if I went to "additional drivers" and installed the cedarview ones in the list, it bricked the video.  NOT impressed.  This is exactly the sort of thing I expect to work with ubuntu.

I ended up installing 32 bit linux mint 13 actually.  All the reports I could find for ubuntu involved compiling the kernel.  I saw one of somebody just installing mint 13 and using synaptic to install the cedarview drivers.

That seemed simpler, so what the hell.  It worked.  I suspect that's because most Mint versions are based on a somewhat older less bleeding edge version of ubuntu with an older kernel that could be held.

I never actually tried installing the cedarview drivers with synaptic in xubuntu though.  That may work without compiling the kernel.

BTW ... if you do try mint, I was not impressed with their xfce implementation.  At all.  I actually reinstalled mint with the MATE shell and then just installed xfce from synaptic.  That worked *much* better.

---

