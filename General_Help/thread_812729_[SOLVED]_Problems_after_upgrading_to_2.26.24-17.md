---
title: "[SOLVED] Problems after upgrading to 2.26.24-17"
date: 2008-05-30
forum: General Help
---

### Post by DreamerHxC on 2008-05-30
Hello everyone:

Two or three days ago, Synaptic told me that there was new a new kernel release for Ubuntu, and so I upgraded.
The problem is that now, when I boot Ubuntu with that kernel and I log in, the screen goes white and I just can see the mouse cursor, but I can do nothing; and even, when I try to boot Ubuntu with the old kernel, it is still the same: the white desktop.
I had the same problem when upgrading from Gutsy to Hardy, but I solved it with a clean installation.
I have an ATI Radeon HD2400 Pro.

Any idea?
Thank you very much for your help.

---

### Post by danwood76 on 2008-05-30
The ATI drivers are most probably not loading correctly.

Boot into the -16 kernel and in the apperance options switch the desktop effects to none.
Reboot into your -17 kernel and the desktop should appear.

Load up synaptic and search fglrx, right click on the xorg-driver-fglrx (not 100% sure on the name) and select completely remove.

Reboot and load the -17 kernel again, and then reinstall the package we removed just a second ago.
Now when you reboot into the -17 kernel the drivers should load and you can switch desktop effects back on.

---

### Post by DreamerHxC on 2008-05-30
But if I boot into the -16 kernel, I have the same problem: the white screen and I can't do anything

---

### Post by danwood76 on 2008-05-30
Well ok, another method.

in the -17 kernel, at the login screen.
In the bottom left is a sessions button click that and select 'Failsafe GNOME' login and the desktop should appear.
Then,

[quote=me]
Load up synaptic and search fglrx, right click on the xorg-driver-fglrx (not 100% sure on the name) and select completely remove.
** edit ** And click Apply

Reboot and load the -17 kernel again, and then reinstall the package we removed just a second ago.
Now when you reboot into the -17 kernel the drivers should load and you can switch desktop effects back on.
[/quote]

---

### Post by DreamerHxC on 2008-05-30
OK, it doesn't work, the white screen is also appearing in the failsafe gnome session

---

### Post by danwood76 on 2008-05-30
Ok, lets do it from the terminal then.

Press Ctrl+Alt+F1 to get to a terminal and log in.

Next we remove the fglrx module and reboot:
```

sudo apt-get purge xorg-driver-fglrx
sudo reboot

```
Once booted back up press Ctrl+Alt+F1 again and login again.
Then to reinstall the fglrx do:
```

sudo apt-get install xorg-driver-fglrx
sudo reboot

```
With a bit of luck after this you shouldnt get a white screen, if you do there is something else we can do.

---

### Post by DreamerHxC on 2008-05-30
Still the same. I've observed that after the white desktop with the mouse cursor, the screen goes completely black, as if it were turned off...

---

### Post by DreamerHxC on 2008-05-30
After trying several things, now what I got is loggin, then white screen and then inmediatly ubuntu sends me back to the loggin screen

---

### Post by DreamerHxC on 2008-05-30
Great, I finally got it, don't know exactly how but I did:
I removed old drivers with the failsafe session, I installed a .deb package with fglrx I had from a previous ATI Catalyst driver. With this I could run ubuntu in graphical mode, then I downloaded ATI Catalyst 8.5 drivers and installed the normal way, and now everything is working fine :)
Thanks for your help

---

