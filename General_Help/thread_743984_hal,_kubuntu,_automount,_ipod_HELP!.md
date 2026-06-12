---
title: "hal, kubuntu, automount, ipod HELP!"
date: 2008-04-03
forum: General Help
---

### Post by Jvaldezjr on 2008-04-03
I am having problems, and have had problems with just about every kubuntu release with mounting my ipod.  Whenever I would plug in my ipod- Kubuntu would see it and try to mount it.  I would get the popup window that would show the mounting progress, however it would hang.  When I would check, via the terminal if it mounted, I can see it did.  However since the popup dialong was hanging, I could no longer access my system via Konqueror.  Everytime I opened konqueror I would get a message that the system has stalled.  I can use my ipod with Amarok, however Amarok has to already be running when I plug my ipod in.  Even then, I still have to mount it with my system, then again have Amarok connect to it.  If I don't do it in a precise order, then Amarok is unable to connect to it.

Can someone help me- I'm not sure which package(s) are causing this problem.  Everything else that I automount (cd/dvd, usb keys) do what they are supposed to.  I've upgraded my libgpod library to libgpod-0.6.0, and I still am having problems.

Thanks.

---

### Post by danwood76 on 2008-04-03
Which version Ipod do you have?

---

### Post by Jvaldezjr on 2008-04-03
I have 20 GB ipod with Click Wheel (1st gen 4 ipod) with the monochrome screen.

---

### Post by Jvaldezjr on 2008-04-04
Can anyone help???

---

### Post by Jvaldezjr on 2008-04-08
I have found a workaround.... apparently KDE manages certain media with a file called mediamanagerrc.  It is located here ```
 ~/.kde/share/config/mediamanagerrc
```

When I opened my file, I saw a bunch of information about my Ipod, and how it was handled.  This is what my file showed:
```

[/org/freedesktop/Hal/devices/storage_serial_Apple_iPod_000000C42294_0_0]
automount=true

[/org/freedesktop/Hal/devices/volume_uuid_2589_ABFE]
atime=false
mountpoint=/media/ipod
quiet=false
ro=false
shortname=lower
sync=false
uid=true
utf8=true

[Global]
AutostartEnabled=false

```

I changed the following lines:
```
automount=true to automount=false
```
and
```
quiet=false to quiet=true
```

That way the kernel will mount my ipod when I plug it in, but I won't get the popup window that shows it is being mounted.  I also get an icon on my desktop so I know it is mounted.  The only issue now is removing the device.  The kernel will unmount the device, but I'll get an error message stating that the device was unmounted but not ejected properly. I can still unplug my ipod and there isn't a problem.  This workaround also fixed my problem with Konqueror stalling when I connected my Ipod.

---

### Post by Jvaldezjr on 2008-04-08
I realized that I can safely remove the ipod through the console, by typing in "eject" and then the device or mount point, which will eject it from my system, after it is unmouted.

---

