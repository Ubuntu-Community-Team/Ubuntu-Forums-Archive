---
title: "Black screen when pressing Install Ubuntu or Try Ubuntu without installing"
date: 2013-06-08
forum: General Help
---

### Post by GeekyGamer14 on 2013-06-08
Hello all,

I am trying to get Ubuntu 12.04 onto my computer and when I boot up the LiveUSB (don't have a CD drive), I can see the GRUB boot screen but it doesn't look like it does here: [IMG]https://help.ubuntu.com/community/LiveCD?action=AttachFile&do=get&target=804+Live+2+.png[/IMG]

Anyways, when I click on it, it just goes to a completely blank screen. No sound or anything. I have tried the acpi=off method and several others. None have worked. I have also tried the wubi install. Here are my specs:

[TABLE="width: 500"]
[TR]
[TD]Motherboard[/TD]
[TD]MSI MS-7786[/TD]
[/TR]
[TR]
[TD]RAM[/TD]
[TD]16 GB[/TD]
[/TR]
[TR]
[TD]OS (currently)[/TD]
[TD]Windows 8 Enterprise 64 Bit
[/TD]
[/TR]
[TR]
[TD]Processor[/TD]
[TD]AMD A8-3870 (3.8 GHz)
[/TD]
[/TR]
[/TABLE]

Yeah, it's custom built.

---

### Post by GeekyGamer14 on 2013-06-08
Nobody?

---

### Post by Bashing-om on 2013-06-08
[COLOR=#000000]GeekyGamer14; Hi !

One gets that screen (or similar) IF one depresses a key as soon as bios screen clears ->language screen (escape key accepts defaults) and the next screen is as you have posted.
From the booted desk top when one activates the "install" icon, the system goes direct to the installer.

In that "boot options" screen try the f6 option, and choose "nomodeset"; see if that boots ya to the "try ubuntu"  desktop, then play with ubuntu to insure all devices function.

edit: A delayed hearty Welcome to the forum.
[/COLOR][INDENT=2][COLOR=#000000]
hope this helps

[/COLOR][/INDENT]

---

### Post by Sef on 2013-06-08
Have you clicked on, check CD for defects?

---

### Post by GeekyGamer14 on 2013-06-08
Yes I have, and nothing but a blank screen, and I tried re-downloading the ISO many times.

---

### Post by GeekyGamer14 on 2013-06-08
> **Bashing-om said:**
> [COLOR=#000000]GeekyGamer14; Hi !

One gets that screen (or similar) IF one depresses a key as soon as bios screen clears ->language screen (escape key accepts defaults) and the next screen is as you have posted.
From the booted desk top when one activates the "install" icon, the system goes direct to the installer.

In that "boot options" screen try the f6 option, and choose "nomodeset"; see if that boots ya to the "try ubuntu"  desktop, then play with ubuntu to insure all devices function.

edit: A delayed hearty Welcome to the forum.
[/COLOR][INDENT=2][COLOR=#000000]
hope this helps

[/COLOR][/INDENT]


As I said here:

> **GeekyGamer14 said:**
> ...it doesn't look like it does here: [IMG]https://help.ubuntu.com/community/LiveCD?action=AttachFile&do=get&target=804+Live+2+.png[/IMG]...



I don't get anything other than Install Ubuntu, Try Ubuntu without installing, or Check disk for defects (Tried that). So that above is what I don't have.

---

### Post by Bashing-om on 2013-06-08
[COLOR=#000000]GeekyGamer14;
Certainly not the norm. 
What machine - and the machines specs - are you attempting to install what version/distro on ? Perhaps we can advise better with additional info ?
[/COLOR][INDENT=2][COLOR=#000000]
still try'n to help

[/COLOR][/INDENT]

---

### Post by GeekyGamer14 on 2013-06-09
> **Bashing-om said:**
> [COLOR=#000000]GeekyGamer14;
Certainly not the norm. 
What machine - and the machines specs - are you attempting to install what version/distro on ? Perhaps we can advise better with additional info ?
[/COLOR][INDENT=2][COLOR=#000000]
still try'n to help

[/COLOR][/INDENT]


Custom built, specs up top, version 12.04 AMD64

---

### Post by Bashing-om on 2013-06-09
[COLOR=#000000]GeekyGamer14;

Should be smooth as silk, your system is very similar to what I am running;
Windows_8 -> we looking at secure boot and/or UEFI as factors preventing booting other operating systems ? 
Old ATI card ? switchable graphics cards ? dual graphics cards ?
[/COLOR][INDENT=2][COLOR=#000000]
where there are solutions there are no problems[/COLOR][/INDENT]

---

### Post by GeekyGamer14 on 2013-06-10
Wow, I am dumb... I always boot into my boot options to make sure it boots into the LiveUSB. There were my hard drives and two other options:

UEFI: SMI USB STICK

and

SMI USB STICK.

I was choosing UEFI. I need to legacy boot... I FIXED IT! I'm closing the thread now.

---

### Post by GeekyGamer14 on 2013-06-10
Nevermind, guess I can't close my own thread :P

---

### Post by Bashing-om on 2013-06-10
[COLOR=#000000]GeekyGamer14; outstanding !

This secure boot and UEFI situations are driving everyone nuts. Particularly us old farts who have not encountered it ! It is a pain to keep track of how the disk(s) are formatted and the booting structure within bios....

All is well that ends well !

To mark the thread "solved":
[/COLOR]Interim method:
> Go to the first post in your thread. Click on "Edit Post". Now click on the orange "Go Advanced" button. In the advanced editor change the prefix to "SOLVED". Now click on the orange "Save Changes" button.

---

