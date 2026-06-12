---
title: "Black screen after login"
date: 2014-12-28
forum: General Help
---

### Post by jwfox on 2014-12-28
Up front here - This PC is actually running Mint 17.1 Mate, not straight ubuntu. Just in case that makes a difference. I posted this on the Mint forum, but it's not as active or helpful as this one, so I figured I'd give it a shot. Google isn't helping. Right now, I'm booting from USB.

Anyhow, the boot process appears to work normally. I get the login screen at normal resolution. Everything looks honky-dory until after I type in my password.

Black screen with mouse cursor. I can move the mouse cursor around the field of black, but that's pretty much all I can do.

dmesg shows this:
```

[   22.171087] vboxdrv: module verification failed: signature and/or  required key missing - tainting kernel
[   22.174880] vboxdrv: Found 4 processor cores.
[   22.175407] vboxdrv: fAsync=0 offMin=0x1d2 offMax=0x20a9
[   22.175987] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
[   22.175990] vboxdrv: Successfully loaded version 4.3.20 (interface 0x001a0008).
[   22.383604] vboxpci: IOMMU not found (not registered)
[   22.712215] init: plymouth-stop pre-start process (1809) terminated with status 1

```

~/.xsession-errors shows this:
```

syndaemon: no process found
/etc/mdm/Xsession: Beginning session setup...
localuser:jfox being added to access control list
Script for none started at run_im.
Script for auto started at run_im.
Script for default started at run_im.
Failed to connect to the VirtualBox kernel service
Failed to connect to the VirtualBox kernel service
Failed to connect to the VirtualBox kernel service
Failed to connect to the VirtualBox kernel service
Failed to connect to the VirtualBox kernel service
Script for none started at run_im.
Script for auto started at run_im.
Script for default started at run_im.
x-session-manager[1964]: CRITICAL: We failed, but the fail whale is dead. Sorry....

```

I haven't done anything out of the ordinary, just system updates. Notebook PC, Asus K55a, i5, integrated Intel video, HD4000.

I don't think it's a video driver issue, because the graphical login screen displays just fine.

In any case, advice would be appreciated.

Tried deleting ~/.Xauthority and rebooting, no joy, same black screen.
Created a new user, new user has same problem.

---

### Post by phidia on 2014-12-28
Welcome to the ubuntu forums. The line in your output "Failed to connect to VirtualBox kernel service" will provide a lot of hits if searched.
I found [this thread]("http://forums.linuxmint.com/viewtopic.php?t=105824&f=46") at the mint forum which possibly relates? Check it out.

---

### Post by HermanAB on 2014-12-28
"I don't think it's a video driver issue, because the graphical login screen displays just fine."
Nope.

At startup the system uses a generic driver, then when you log in, it detects the hardware and loads a better driver.  Things also reconfigure on the fly when you plug a separate screen or projector or some such in.

So, the trouble is that your video hardware detection goes wrong somehow.  You can force it by creating and xorg.conf file and configuring it manually.

You may also be able to debug the problem by plugging a second external screen into a VGA port - it may come up.

---

### Post by jwfox on 2014-12-28
> **phidia said:**
> The line in your output "Failed to connect to  VirtualBox kernel service" will provide a lot of hits if searched.


Yeah I went ahead and purged virtualbox with no change.

> **HermanAB said:**
> 
At startup the system uses a generic driver, then when you log in, it detects the hardware and loads a better driver.  Things also reconfigure on the fly when you plug a separate screen or projector or some such in.

So, the trouble is that your video hardware detection goes wrong somehow.  You can force it by creating and xorg.conf file and configuring it manually.

You may also be able to debug the problem by plugging a second external screen into a VGA port - it may come up.

Good to know...  At least it gives me somewhere to look.

---

