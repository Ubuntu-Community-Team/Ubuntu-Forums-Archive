---
title: "No more GUI"
date: 2008-02-02
forum: General Help
---

### Post by WIndsorcalgarian on 2008-02-02
I was having trouble with my soundcard, i was getting no sound under any circumstances so i went to the troubleshooting part of this website and tried some stuff there and then it said to reboot and when i did so Ubuntu loaded with a command line interface with no GUI, cant run anything that isnt text based. How can i get my GUI back?

please help

-kent

---

### Post by taurus on 2008-02-02
What happens when you run this command from a prompt?

```
startx
```

---

### Post by WIndsorcalgarian on 2008-02-02
thanks that worked now any chance you have any ideas on the sound problem?

---

### Post by WIndsorcalgarian on 2008-02-02
Ok that got my GUI to work but what do i do to get my login screen back and also when im in the GUI i cant restart or shut down i have to log out and then do it manually,

---

### Post by taurus on 2008-02-02
Try installing gdm again so it will boot into GUI login screen.

```
sudo apt-get update
sudo apt-get install gdm
sudo /etc/init.d/gdm start
```

And for your soundcard.  I have no idea which one you have so can't do much there.

---

### Post by WIndsorcalgarian on 2008-02-02
Great dont know how that got uninstalled, the soundcard i have:

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
        Subsystem: Toshiba America Info Systems AC97 Data Fax SoftModem with SmartCP
        Flags: bus master, fast devsel, latency 0, IRQ 22
        Memory at d0340000 (64-bit, non-prefetchable) [size=16K]

---

