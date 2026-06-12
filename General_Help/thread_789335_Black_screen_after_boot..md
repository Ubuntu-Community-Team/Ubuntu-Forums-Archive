---
title: "Black screen after boot."
date: 2008-05-10
forum: General Help
---

### Post by NateTheGr8 on 2008-05-10
I have Ubuntu 8.04 desktop and after I downloaded some driver for my X1950GT gpu it just shows a black screen after the Ubuntu loading screen. I tried doing Ctrl+Alt+F1 but that didn't do anything. I just got Ubuntu and I have no clue what to do...

---

### Post by TeoBigusGeekus on 2008-05-10
Reboot and enter recovery mode with grub.
Then type
```
sudo dpkg-reconfigure xserver-xorg
```

When finished, type
```
sudo reboot
```

---

### Post by NateTheGr8 on 2008-05-10
Thanks man, it's back to normal.

Are there any working drivers for X1950GT?

---

### Post by TeoBigusGeekus on 2008-05-10
Open synaptic package manager and install envy. Let it choose the drivers for you.

---

### Post by ghost_ryder35 on 2008-05-10
> **TeoBigusGeekus said:**
> Open synaptic package manager and install envy. Let it choose the drivers for you.
Envy is awesome, you could also try 
System, Administration, Hardware Drivers and see if there is a driver for your card there :)

---

