---
title: "How can I improve boot times?"
date: 2008-04-06
forum: General Help
---

### Post by Raccoon1400 on 2008-04-06
My laptop with gutsy, 2 GB of ram, and a 1.6GHz core 2 duo.
It boots in about a minute.  How can I improve this?
With bootup manager, I disabled some services. Here is what is left.

acpid
hal
dbus
dnsmasq
cupsys
makedev
nvidia-kernel
hotkey-setup
netapplet
powernod
rsync
vboxdr
consolekit
avahi-daemon
dhcdbd
gdm
atd
cron
laptop-mode
acpi-support

---

### Post by alejo0823 on 2008-04-06
check this [http://www.techthrob.com/tech/preload.php](http://www.techthrob.com/tech/preload.php) I think this is what you are looking for, I found it in digg.

---

### Post by Rocket2DMn on 2008-04-06
Here is how you can reprofile the boot sequence - [http://ubuntuforums.org/showthread.php?t=254263](http://ubuntuforums.org/showthread.php?t=254263)
There is some extra stuff there but the "profile" part for GRUB is definitely useful.

---

### Post by Raccoon1400 on 2008-04-07
> **Rocket2DMn said:**
> Here is how you can reprofile the boot sequence - [http://ubuntuforums.org/showthread.php?t=254263](http://ubuntuforums.org/showthread.php?t=254263)
There is some extra stuff there but the "profile" part for GRUB is definitely useful.

I'm not sure this is quite what I'm looking for. I think it is just loading stuff I don't need.

---

### Post by Raccoon1400 on 2008-04-07
> **Raccoon1400 said:**
> I'm not sure this is quite what I'm looking for. I think it is just loading stuff I don't need.

I take it back. It appears to have taken six seconds off my boot.
I still think it is loading stuff I don't need.

---

### Post by Raccoon1400 on 2008-04-07
If I could reduce the amount of time gnome took to start.
It takes at least 10 sec right now.

---

