---
title: "Can you access the BIOS from the grub menu"
date: 2015-03-21
forum: General Help
---

### Post by bfuzze on 2015-03-21
I'm in a peculiar situation where I can not access my BIOS.  I think it is because fast boot is enabled.  I think I can probably flash to reset the default BIOS settings, but before I go to that extreme is there a way to add a grub boot menu option to access the bios?  

I've seen some installers can take you directly to the bios, but that is usually from bootable media (USB/CD).  I'd take that option as well if anybody knows how to do it, keeping in mind that I only have USB on this computer (no disk drives). 

Is there any other way to access the bios other than at startup, cause I'm pretty sure that path is out without a reflash?


Background:  In order to boot from a USB, for this laptop you need to disable the UEFI, but I found out too late that in order to access the bios without UEFI you have to disable fast boot from within windows.  Now I've got the new OS installed, no access to bios though.

Thanks.

---

### Post by dino99 on 2015-03-22
why are you so scary about resetting your bios to default values ? It's a good reason for reviewing the parameters.
the bios process is the first starting, way before the grub one, and can only be called by hitting some key(s) (usually 'del' or 'F1' see the mobo doc)
if you cant hit that key for some reason, then force a bios reset to default value by: powering off (remove cord), then remove the bios battery and wait a dozen seconds before pulling back that battery. On next reboot, reset the bios values as you wish/need.
note: also check if a newer bios version is available

---

### Post by buzzingrobot on 2015-03-22
Short answer: No.

The only time the BIOS menu is accessible is immediately after a system is powered on or does a hard reboot. Once the OS boots, you can't access the BIOS.

The BIOS is firmware, i.e., code burned into the motherboard. The BIOS is in control of a machine when it first powers up.  After that, the BIOS hands over control to the code that boots the operating system.That's the bootloader. (This is standardized on all hardware using the standard PC architecture.) In Linux, that code is Grub.

To access the BIOS settings, you need to apply a particular keystroke as the system boots, as 9d9 outlined. Just boot and immediately begin tapping on the key, repeatedly. Different BIOS vendors use different keystrokes.

---

### Post by bfuzze on 2015-03-24
Thanks.  Yeah I know the purpose/nature of the bios.  Resetting defaults is not scary, but re-flashing can be catastrophic so I consider it extreme.  In my current scenario the usual key sequences don't catch (known problem with this laptop), especially if fast boot is enabled.  

Out of the box, **with this system the only way to access the BIOS is to hold the shift key while hitting restart from windows 8, at which point you're rerouted to a UEFI utility which eventually will allow you to access the BIOS**.  The goal was to change boot-priority to the USB, but this wasn't sufficient.  I needed to disable UEFI.  Normally you would switch off fast boot inside the BIOS at the same time as disabling UEFI, but I didn't see the fast-boot option in there (I saw secure boot, already disabled), which is how I got into this predicament.  Later, I read that you're supposed to turn off fast-boot from inside Windows (which seems weird).  

My hope was that someone could suggest a **utility or grub settings, similar to the UEFI utility** I mentioned that would get me into that workflow.  Maybe I'll give boot repair a shot.

Thanks for the input.

PS Sorry for the late response, thought I had email subscribed to this thread, but...

---

### Post by oldfred on 2015-03-24
Do you have this entry in grub?
If you have UEFI boot then you should.

```
### BEGIN /etc/grub.d/30_uefi-firmware ###
menuentry 'System setup' $menuentry_id_option 'uefi-firmware' {
    fwsetup
}
### END /etc/grub.d/30_uefi-firmware ###

```

Some systems will "slow" boot or give you time to get into UEFI on a total reboot or cold boot from power shutdown.

My new UEFI motherboard had settings for fast boot on for both cold boot and warm boot and timeout setting for both. I turned off fast boot for code reboot, and set a 3 sec delay on warm boot and 3 second on grub menu. The 6 sec reboot is now a huge part of my reboot as SSD is very fast, but I want the chance to get into UEFI if needed.

---

### Post by bfuzze on 2015-03-26
Thanks oldfred, that's more along the lines of what I was looking for.  I took a look last night and I do see this config file, but the preceding logic that would enable this option must be failing, most likely because I disabled UEFI.  Nonetheless, this is really good to know for the future.  Thanks!

---

