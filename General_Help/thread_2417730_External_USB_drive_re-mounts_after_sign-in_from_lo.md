---
title: "External USB drive re-mounts after sign-in from lock"
date: 2019-04-26
forum: General Help
---

### Post by echobox on 2019-04-26
Hi, all, I have an external USB drive attached to my regular Ubuntu 19.04 machine. I have been unmounting it when not in use but leaving it attached. I have to do this, as the drive sometimes causes the system to freeze. I've found the solution to my freezing problems was simply to keep the drive unmounted when not in use. It is just for backups and works fine if I mount it, do my backup, and then unmount it.
The problem is that, if I unmount it and then lock my screen, when I return and unlock my screen, I find the drive has been mounted again. I'm worried this will lead to more freezes, so my solution at the moment is simply to unmount it and unplug it from the computer when not needed.

But it seems that, if I unmount it, it should be able to maintain its unmounted state until I myself mount it again. Anyone have any idea why it mounts on its own after unlocking my system? Thanks. :)

---

### Post by #&amp;thj^% on 2019-04-26
Automount does that...
This may be more than you wanted, but it works and once accustom to doing it this way>>>It's not so bad.

Check your usb flash name with:
```

lsusb
```

my sandisk example:
```

Bus 003 Device 005: ID 0781:540e SanDisk Corp. Cruzer Contour Flash Drive
```

Now i know my sandisk is on bus 003 and device 005
We have to check your usb bus and port number with:
```

lsusb -t

    Bus 03.Port 1: Dev 1, Class=root_hub, Driver=xhci_hcd/14p, 480M
    |__ Port 5: Dev 5, If 0, Class=Mass Storage, Driver=usb-storage, 480M
```

Now we know that bus 3 device 5 is on port 5 so we can go to :
```

cd /sys/bus/usb/drivers/usb
```

and disable the port:
```

sudo tee unbind <<< "3-5" 
```

To enable port:
```

sudo tee bind <<< "3-5"
```

Good Luck

---

### Post by DuckHook on 2019-04-26
Some external drives have automatic spindown and sleep circuitry that might confuse your OS if it is expecting instant availability. I see three options:

[LIST=1]
[*]Limit power management or eliminate it altogether [using hdparm]("http://manpages.ubuntu.com/manpages/trusty/man8/hdparm.8.html"). CAUTION hdparm and USB drives are a fragile mix. Older USB HDDs do not support it at all. NEVER turn off power in the course of a long hdparm process or risk bricking you drive.
[*]Use [autofs]("https://help.ubuntu.com/community/Autofs") which automatically spins down and unmounts drives after a period of inactivity. The system hooks used by autofs add robustness by forcing the OS to be patient and wait for spin-up before accessing the drive.
[*]The "best" solution is to physically unplug the drive when it is not is use. No way for it to cause problems that way. In dealing with computers, simple is always better.
[/LIST]

---

### Post by echobox on 2019-05-09
I want to thank you both for your advice.
I found out that the real problem was my monitor. It's a 4K Dell UltraSharp 27". I switched off the sleep mode on it, and everything cleared up.
I keep the external USB drives hooked up and active with a crontab that runs touch on a hidden file very five minutes. I know it'd be better if I didn't have these drives always connected, but, until I can get a new internal hard drive with more capacity, this will have to do. And it works.
It's been several days, and I've seen no problems. I think it must be the sleep mode on the monitor that was to blame.
Kudos again for your help. :)

---

