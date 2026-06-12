---
title: "Splash at boot, yet again"
date: 2013-05-03
forum: General Help
---

### Post by jwfox on 2013-05-03
I've searched the forums, and turned up many threads about boot-splash problems, but none of them realy seem to apply.

I'm running 12.04 on an Asus K55A notebook.  Not dual-booting or anything; I swapped in a fresh new HDD and loaded 12.04 from the LiveCD. Everything installed and worked except the SD card reader. Got that working. Spent a week or so doing updates, installing packages, configuring things, etc, and everything was peachy keen.

Problem started after I used Clonezilla to back up the drive. Strange, because all I did was image it to a USB drive.

But here's the thing that is annoying me... It's just the initial boot display/splash, and it doesn't seem to matter whether it's a cold-boot from power-off, or otherwise:

BEFORE the problem started:
Solid purple screen for ~2-3 seconds
Purple screen with "ubuntu" and animated dots for ~5-7 seconds
Login screen

AFTER the problem started:
Solid purple screen for ~ 8-9 seconds
Quick flash of the "ubuntu" against the purple
Quicker flash of the 'animated dots', but not animating, and displayed at the left of the screen
Login screen

WTF?

It's annoying. I could just disable the splash, I guess. I don't mind having text scroll while the system boots. But I'd prefer to understand and fix the intended behaviour.

Thanks to anyone who can assist.

---

### Post by matt_symes on 2013-05-03
Hi

If you boot into an older kernel, do you still have the same problem ?

Kind regards

---

### Post by jwfox on 2013-05-04
Funny thing... 

Don't see any option to boot a different kernel. No Grub menu. Purple screen, then brief wonky flash of what shoud be the regular boot-splash, then the login screen. Holding <shift> during boot doesn't give me a menu, or seem to have any other effect.

Please talk to me like I'm a total newbie, and I'm four years old.

[edit]
Ummm, no, I wasn't trying to be sarcastic there...  I would actually prefer it anyone willing to help starts with the assumption that I'm relatively clueless, because such an assumption wouldn't be far off.

Should I have posted this in a different forum? By all means, feel free to correct any misbehavior on my end.

---

### Post by matt_symes on 2013-05-04
Hi

Sounds like you may only have one kernel installed at the moment then.

I'm not sure how cloning the hard drive would cause this issue and i suspect the cause is what different.

That purple splash screen you see is part of plymouth. 

The first thing i would try is to update a file called initramfs.

Open a terminal and type

```
sudo update-initramfs -u
```

Enter your password. It will not be echoed to the screen. This is normal.

Reboot your PC. Do you still have the same issue ?

BTW: I forgot to say "Welcome to the forums" :D

Kind regards

---

### Post by jwfox on 2013-05-05
> **matt_symes said:**
> Hi
I'm not sure how cloning the hard drive would cause this issue and i suspect the cause is what different.


I agree, it's probably just coincidental that it started after I cloned it.

The update-initramfs command ran successfully, but didn't appear to change anything. I tried installing a different boot-splash from gnome-look.org, in the hopes that it would rewrite something that might correct it.  The new splash worked, but exhibits pretty much the same behavior. Instead of purple, it's a black screen, then a quick flash of the gnome-foot, then a quicker flash of the progress-bar on the left of the screen, then the login prompt.

---

### Post by jwfox on 2013-05-05
Well, it works now. [edit: No, it doesn't. See below] [edit again: Maybe it does. Further below]
  Here's what I did:
```

sudo apt-get install --reinstall plymouth plymouth-label libplymouth2
sudo apt-get install --reinstall plymouth-theme-ubuntu-logo
sudo apt-get install --reinstall plymouth-theme-ubuntu-text

```

Probably overkill, but it fixed it.  Would still like to know what made it go all wonky in the first place, but I suppose that's unimportant now.

[edit:]
-=-=-=-=-=-=-=-=-=-=-=-=-=-=-
I spoke too soon. 

It appeared to be fixed for exactly one reboot. Now it's back to a blank screen for a long while, and a quick blink of what should be the splash immediately before the login window appears.  Progress bar is in the right spot now, instead of being pulled all the way to the left. Not that a progress-bar is of much use when it only displays briefly right before the progress is complete.

Enabling/disabling "Fast Boot" in the BIOS has no noticeable effect.

[edit again:]
-=-=-=-=-=-=-=-=-=-=-=-=-=-=-
```

sudo -s
 echo FRAMEBUFFER=y >>/etc/initramfs-tools/conf.d/splash
 update-initramfs -u
exit

```

Worked, we'll see if it lasts.

---

### Post by matt_symes on 2013-05-05
Hi

> 
[edit again:]
-=-=-=-=-=-=-=-=-=-=-=-=-=-=-
 	Code:

 	
sudo -s  echo FRAMEBUFFER=y >>/etc/initramfs-tools/conf.d/splash  update-initramfs -u exit 
Worked, we'll see if it lasts.

I believe this can sometimes cause problems, if using the nvidia/other driver.

If you get system installability then suspect this.

Kind regards

---

### Post by jwfox on 2013-05-05
Thanks, I'll keep that in mind.  System has onboard intel graphics. Just now noticed that System Settings->System->Details has "Graphics" listed as "Unknown". I'd be inclined to believe that might be part of the problem, but I don't know...  Because it WAS working initially.

I welcome other suggestions, if the framebuffer fix might be likely to cause problems.

[edit]
Installed mesa-utils, and now System Settings reports graphics as "Intel Ivybridge Mobile:.

[edit again:]

This is interesting:
```

~$ sudo hwinfo --framebuffer
[sudo] password for ------: 
> hal.1: read hal dataprocess 4262: arguments to dbus_move_error() were incorrect, assertion "(dest) == NULL || !dbus_error_is_set ((dest))" failed in file ../../dbus/dbus-errors.c line 282.
This is normally a bug in some application using the D-Bus library.
libhal.c 3483 : Error unsubscribing to signals, error=The name org.freedesktop.Hal was not provided by any .service files

```

---

