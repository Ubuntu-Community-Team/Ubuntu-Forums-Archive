---
title: "Suspend problems with lirc_dev"
date: 2007-04-13
forum: General Help
---

### Post by broxtor on 2007-04-13
I've got a desktop running Feisty which I would like to be able to suspend. But I'm having some issues with that. When I'm trying to suspend the computer I get the message:

```
one task refusing to freeze: lirc_dev
```

In /var/log/messages I get the entry:

```

kernel: [  372.372000] Stopping tasks ...
kernel: [  392.532000] Restarting tasks ... <4> Strange, lirc_dev not stopped

```

I edited /etc/default/acpi-support and added MODULES="lirc_dev", but that doesn't help.

In fact, I'm afraid that /etc/default/acpi-support isn't read at all. When I put the computer to suspend the screen goes off and after 20 seconds, the system comes back online. But at that point the screen is locked. This is strange because in /etc/default/acpi-support I set LOCK_SCREEN=false.

Can someone give me some pointers on how to solve this?

---

### Post by energiya on 2007-04-14
Did suspend worked for you before installing lirc? Because suspend has some problems working with some videocards or other specific hardware.

---

### Post by ifross on 2007-04-23
I have the same problem! It is really annoying, its late now, but I'll look into it tomorrow... (Althouigh I'm not very good with linux yet so I doubt it will be much use.) I'll search on the internet as well...

---

### Post by Naoi on 2007-10-25
I am having this exact same problem with 7.10 Gutsy and hoped someone has some new insight on this.

I just made a MythTV box and can get it to go into suspend as long as the remote control package (lirc) isn't installed, once I install it (via Mythbuntu)  it won't suspend anymore, it sits there for about 20 seconds then displays the message about lirc_dev refusing to freeze.

I had the same observations as the original poster, adding lirc_dev to the MODULES list in /etc/default/acpi-support didn't change anything, and it  ignores setting LOCK_SCREEN=false because the screen is locked (wants a user name & password) once suspend fails to occur, which also makes me think that the entire file isn't being used somehow.

I also tried adding lirc_dev to the MODULES_WHITELIST in /etc/default/acpi-support to leave it in the kernel over suspend/resume and it made no difference.

Would compiling  lirc_dev into the kernel help? Not that I know how how to do that lol

My goal is to have MythTV work like an off the shelf DVR, and getting suspend to work with a remote is a big part of that. 

 I haven't figured out how to get resume to work without having to press the front panel power button but that's the next mountain!

I've googled everything I can think of to find a solution elsewhere and have had no luck, so any help would be greatly appreciated. :)

---

### Post by OtherHand on 2007-11-24
I was wondering if anyone had figured out how to solve this lirc_dev problem?

I have run into the identical issue and searching turned up this thread.  I have a VIA EPIA MII 10000 motherboard, running Gutsy 7.10, that I'm trying to use as a dedicated HTPC and PVR.  When not watching  movies I'd like to have it suspend or hibernate.  It appears the system can't freeze lirc_dev, which keeps it from going into sleep modes, so I have to do a full shutdown.  Very frustrating!

I'm pretty much a Linux noobie, but have lots of Windows experience.

I've tried sudo kill (PID for lirc_dev) and I don't get an error message, but the process stays active.

Thanks much for any help!!

---

### Post by chosebin on 2007-12-03
hi,

After a week, I managed to get suspend-to-ram to work on Ubuntu 7.10! You cannot kill lirc_dev, because it is a kernel module. However, you can unload it with the rmmod command:

- sudo su
- rmmod lirc_dev

If you get an error similar to:

 ERROR: Module lirc_dev is in use by lirc_i2c

It means lirc_i2c (or another module specific to your hardware) depends on lirc_dev, and you need to unload it first. To do this:

- sudo su
- rmmod lirc_i2c /* whatever dependency you get in the error message */
- rmmod lirc_dev

By running those commands, you should be able to suspend your machine, if you don't have a driver problem like I had for a week :) After a resume, you can reload those modules with:

- sudo su
- modprobe lirc_dev
- modprobe lirc_i2c /* whatever dependency you get in the error message */

If suspend-to-ram works for you after unloading lirc_dev, you will probably want to unload automatically those modules when you suspend your machine and load them automatically when you resume your machine. To do this, in the file /etc/default/acpi-support, change line:

- MODULES=""

by

- MODULES="lirc_i2c lirc_dev"

Be careful to insert lirc_i2c (or anything else) before lirc_dev.
--------------------------------------------------------------------------------------
Nices resources to know on Ubuntu 7.10 and related to ACPI S3 (Suspend-to-Ram)

/etc/acpi/ -> scripts for ACPI
/etc/default/acpi-support -> configuration file for scripts in /etc/acpi
/usr/lib/hal/scripts/linux/hal-system-power-suspend-linux -> script executed by gnome to suspend to ram
/proc/acpi/alarm -> modify to set a wakeup time (if supported by mobo)

---

### Post by OtherHand on 2007-12-04
Thanks very much!  That fixed the problem perfectly.  The lirc_i2c module wasn't letting go, and this hung up the lirc_dev module.  All is good now......

---

### Post by Naoi on 2007-12-08
Thanks very much for the tip chosebin ! :)

I can now suspend my machine which is great, but ... (why is there usually a but ? :) )

MythTV doesn't work after resuming from suspend :confused:

When I restart MythTV I see the mythfrontend.real process is running in the System Monitor but nothing is displayed.

If anyone knows why please respond, my first efforts at Google haven't turned up any answers but if I find any I will post them. :)

BTW  I found out how to get rid of the locked screen upon resuming.  Under System Tools-> Configuration Editor -> apps-> gnome-power-manager->lock there's a setting called "suspend" that was checked, when I unchecked it I no longer had to enter my password to get back to the desktop.

Thanks again! :)

---

