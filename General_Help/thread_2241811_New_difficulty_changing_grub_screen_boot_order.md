---
title: "New difficulty changing grub screen boot order"
date: 2014-08-28
forum: General Help
---

### Post by 2CV67 on 2014-08-28
I used Grub Customizer OK for several years, to control the order of various OS's on the grub screen.

Now, I just got a new PC with W8.1 & installed Ubuntu 14.04.1 as dual-boot (in sda7).
Happily, the grub screen showed Ubuntu first & Windows later.
So far - so good.

Then, I installed Ubuntu again, in a little partition (sda9) as a back-up & lifebelt.
As expected, the grub screen then put the sda9 Ubuntu at the top, which is not what I want.
Actually, it put W8 next & sda7 Ubuntu later.

Now I know I can dig into /etc/default/grub & tell it to boot sda7, but I prefer to see the options in the order sda7 / sda9 / W8.

So I installed the latest Grub Customizer (in sda7) & let it run, expecting it to find the same order I see on the grub screen (sda9 / W8 / sda7).
But no - it shows me the order (sda7 / W8 / sda9)!!!

I tried shifting W8 down to the bottom in GC, as at least a start, and saved that change.
But on rebooting, the grub screen still shows sda9 / W8 / sda7...

Conclusion: Grub Customizer is not seeing what the grub screen says, nor having any effect on the grub screen.

All suggestions welcome!

Thanks!

---

### Post by grahammechanical on 2014-08-28
When you installed Ubuntu into sda7 Grub was put in charge of the boot process. Grub will look for its configuration files in /boot on sda7. and Ubuntu was at the top of the list.

When you installed Ubuntu into sda9 It put its Grub in charge of the boot process and will look for its configuration files in /boot on sda9, and the Ubuntu of sda9 became first in the boot menu.

The solution? Load into the Ubuntu of sda7 and run these two commands.

```
sudo update-grub
sudo grub-install /dev/sda
```

Or, run Grub Customizer from Ubuntu on sda7 and make your changes and this time save the work and then use a menu in Grub Customizer to install to the MBR of sda.

It is a two step process. 1) Update the Grub configuration file. 2) Re-install the Grub of sda 7 into the MBR of sda.

If we want to change things in the Grub menu we need to make sure that we are making changes to the Grub configuration files of the version of Ubuntu that has its Grub in the MBR.

Regards.

---

### Post by 2CV67 on 2014-08-28
Brilliant!

Thank you very much for a clear answer which works!  :D

---

