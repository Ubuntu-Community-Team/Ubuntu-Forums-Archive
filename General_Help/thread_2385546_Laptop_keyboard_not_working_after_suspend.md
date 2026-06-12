---
title: "Laptop keyboard not working after suspend"
date: 2018-02-21
forum: General Help
---

### Post by enekoalfer on 2018-02-21
Hi!

I recently reinstalled Ubuntu 16.04 LTS (x64) on my SONY VAIO VPCEH laptop (dual boot with Windows 10, also installed by me). Whenever I suspend the computer by closing the cover and I turn it on again, the keyboard won't respond (the trackpad does work).

Yesterday I tried to edit the GRUB file (sudo nano /etc/default/grub) and changed the line

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```

by adding

```
 GRUB_CMDLINE_LINUX_DEFAULT="quiet splash atkbd.reset" 
```.

Then I updated the GRUB and rebooted.

So, the problem seemed to be solved but today I discovered that it only works if the laptop is suspended for short periods of time. If it is suspended long enough (5 minutes for example), the keyboard won't work, so I have to reboot in order to use it again.

Maybe this has something to do with the swap partition, as I formatted the partitions myself and I have the feeling that the swap partition is not allowing the system to hibernate correctly (I set it at 5GB, and my laptop has 4GB of RAM), but I am not sure if that does even make sense.

I hope someone finds the solution to this issue. Until then, thanks in advance for reading/trying.

Have a nice day! :KS

P.D.: Sorry if I wrote something incorrectly, English is not my first language!

---

### Post by alvaropag on 2018-08-04
I have the same problem, I tried i8042.reset on [COLOR=#000000][FONT=&quot]GRUB_CMDLINE_LINUX_DEFAULT[/FONT][/COLOR] but the problem persists. 
For the laptop keyboard to work I have to plug a usb keyboard, the caps lock led will blink and then the laptop keyboard will work again.

---

