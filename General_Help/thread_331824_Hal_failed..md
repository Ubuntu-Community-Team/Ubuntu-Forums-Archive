---
title: "Hal failed."
date: 2007-01-05
forum: General Help
---

### Post by nadavvin on 2007-01-05
When gnome load I get message box which hal failed.

How do I fix it?

---

### Post by Scorpuk on 2007-01-05
What changes did you do before this happened?


Any new programs starting on bootup that use a device connected to the USB port?

---

### Post by nadavvin on 2007-01-05
I don't know.

I have this problem from long time and now I want to fix it.

The exact error nessage is: "failed to initialize HAL!"

---

### Post by bapoumba on 2007-01-05
Hi,
there is a bug report :
[https://launchpad.net/ubuntu/+source/hal/+bug/44874]("https://launchpad.net/ubuntu/+source/hal/+bug/44874")
Can you find anything helpful in there ? (last messages are fairly recent).

---

### Post by perky on 2007-01-07
G'day,

Has anyone found a fix for this prob yet?  I'm getting the same (rather annoying!!) popup every boot ("HAL failed to initialize!").  Consequently, USB devices do not automatically mount.

I'm using Edgy 64bit on an AMD.  Motherboard is an Asus A8n-e (Nforce 4 chipset).

The bug seems similar to _**[this]("https://launchpad.net/ubuntu/+source/hal/+bug/24029")**_, but the debugging steps I followed give different results:

```

andy@andy-desktop:~$ pidof hald
4369
andy@andy-desktop:~$ cd /var/run/dbus
andy@andy-desktop:/var/run/dbus$ ls
pid  system_bus_socket
andy@andy-desktop:/var/run/dbus$ sudo /etc/init.d/dbus restart
Password:
 * Stopping System Tools Backends system-tools-backends                  [ ok ] 
 * Stopping Avahi mDNS/DNS-SD Daemon: avahi-daemon                       [fail] 
 * Stopping Hardware abstraction layer hald                              [ ok ] 
 * Stopping system message bus dbus                                      [ ok ] 
 * Starting system message bus dbus                                      [ ok ] 
 * Starting Hardware abstraction layer hald                              [ ok ] 
 * Starting System Tools Backends system-tools-backends                  [ ok ] 
andy@andy-desktop:/var/run/dbus$ pidof hald
14998

```

The linked bug also makes reference to bug #13333 (says that post 16 has a fix!), but I when I go to this, an evolution bug displays! ](*,) 

Help!

---

### Post by perky on 2007-01-07
Also, I've noticed that that I can manually mount the USB drive via:

```

sudo mount -t vfat /dev/sda1 /media/usb0

```

---

### Post by Len_C on 2007-01-07
Hava a look at [http://www.ubuntuforums.org/showthread.php?t=316907](http://www.ubuntuforums.org/showthread.php?t=316907)

try
sudo update-rc.d -f dbus remove
sudo update-rc.d dbus defaults 12

---

### Post by perky on 2007-01-08
> **Len_C said:**
> Hava a look at [http://www.ubuntuforums.org/showthread.php?t=316907](http://www.ubuntuforums.org/showthread.php?t=316907)

try
sudo update-rc.d -f dbus remove
sudo update-rc.d dbus defaults 12

Thanks!  You are a life saver, this fixed the prob.

---

### Post by Wanderers on 2007-01-08
I have the same problem on my machine, but unfortunately the suggested solution does not fix the problem.  In addition, I cannot manually mount my USB Memory stick either.    Any ideas where to go from here?  This is a very annoying problem as I can basically not use any USB memory sticks!

My USB mouse works fine, by the way.

Thanks!

---

### Post by perky on 2007-01-12
> **Wanderers said:**
> I have the same problem on my machine, but unfortunately the suggested solution does not fix the problem.  In addition, I cannot manually mount my USB Memory stick either.    Any ideas where to go from here?  This is a very annoying problem as I can basically not use any USB memory sticks!

My USB mouse works fine, by the way.

Thanks!

Are any new files created in /dev/ when you plug in the device?  Easiest way to tell is to browse with Nautilus, and take note of the number of items in the status bar before and after your mem stick is plugged in.

---

### Post by nadavvin on 2007-01-15
Unfortunately, I didn't see your posts and I already upgrade to feisty.

now I have bigger problem.

[http://www.ubuntuforums.org/showthread.php?t=338564](http://www.ubuntuforums.org/showthread.php?t=338564)

---

