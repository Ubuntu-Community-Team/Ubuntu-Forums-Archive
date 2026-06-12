---
title: "[Asus E202] freeze at startup"
date: 2015-11-25
forum: General Help
---

### Post by Romain_Cayre on 2015-11-25
Hi everybody :)
First of all, excuse me for my bad English : i'm french and I come here because the french ubuntu community hasn't found a solution to my problem.
I recently bought a notebook called Asus E202S, and I have installed Ubuntu Wily on it. The problem is :
> when the laptop is connected to the power cable, everything works fine and i can access my desktop
> when the laptop isn't connected, ubuntu freezes during startup (at the line : Starting WPA Supplicant...), and i'm forced to do a hard reset.

I also realized that the problem doesn't appear if i Lock the Wifi card in the BIOS Setup, but i would like to use the Wifi function ...
Thanks a lot !

---

### Post by Romain_Cayre on 2015-11-27
up ?

---

### Post by climmu on 2016-01-07
Hi,
french users found a solution to the same issue [URL="https://forum.ubuntu-fr.org/viewtopic.php?id=1948291&p=3"]here.

[/URL]```
sudo cp /etc/default/grub /etc/default/grub.bak
sudo gedit /etc/default/grub
```

In this file, change 
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
to 
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash pci=nomsi"

save

then 
```
sudo update-grub
sudo reboot
```

I hope it help
regards

---

