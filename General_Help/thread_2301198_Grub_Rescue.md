---
title: "Grub Rescue"
date: 2015-10-31
forum: General Help
---

### Post by jsleotti on 2015-10-31
So, a few days ago I tried dual-booting Mint with my Ubuntu install because wanted to see if it was better. Long story short, it wasn't; so I deleted the partition that had Mint on it. When I restart the computer, I get "Grub rescue". Now, I can follow the directions on another post and get it to boot into Ubuntu, but it seems like this is going to do this every time I start my computer since this is the second time I had to do it. How do I make it not do that?

EDIT: If I run:

> [COLOR=#000000]*sudo apt-get update grub*[/COLOR]

I get:

> E: The update command takes no arguments

???

---

### Post by Dennis N on 2015-10-31
update-grub has a hyphen, and there is no apt-get:

**sudo update-grub**

is all you use if you want to update the grub menu.

Based on your account, I think you will need to install grub from Ubuntu in order to boot, not just update.

---

### Post by jsleotti on 2015-10-31
Thank you. I copied it from another site who was obviously wrong. I tried updating it from recovery mode as well, but it produced the same results. How do I reinstall the GRUB on this partition?

---

### Post by Dennis N on 2015-10-31
Assuming you are not using UEFI, boot into Ubuntu as you have done. Then run:

```
sudo grub-install /dev/sda
```

Change sda to the correct drive designation (sdb for example) if necessary, but do not add a partition number, like sda1. 

Then,

```
sudo update-grub
```

You should be back in business.

---

### Post by jsleotti on 2015-10-31
Thanks. I booted into my Live CD and ran boot repair. Worked like a charm.

---

### Post by grahammechanical on 2015-10-31
Do you understand what happened in the first place? It is useful information to know for the next time you want to multi-boot more than one Linux distribution.

The last Linux distribution installs its Grub boot loader which then looks for Grub configuration files in /boot/grub of the OS just installed. So, Linux Mint over-wrote the Ubuntu boot loader and became in charge of the boot process. By deleting that partition you left the Linux Mint Grub in charge of booting but without any configuration files to access.

Next time load into the OS that you want to remain. I assume it will be Ubuntu and run

```
sudo grub-install /dev/sda
sudo update-grub
```

And then delete the partition of the distribution you want to be rid of. For those who are dual booting with Windows and want to remove Linux. First restore the Windows' boot loader before deleting the Linux partitions.

Regards.

---

### Post by yancek on 2015-10-31
> The last Linux distribution installs its Grub boot loader which then  looks for Grub configuration files in /boot/grub of the OS just  installed

That's true if you use one of the auto-install method, Install Alongside but if you use a manual installation (Something Else in Ubuntu and derivatives) you can always install to the partition where the system is installed.  Done this numerous times with various systems.  It's especially useful if you have a system you are using and familiar with (such as Ubuntu) and want to test (such as Mint), install the Mint bootloader to the system partition.  I've seen countless posts such as this because people try the "auto-install" method  and are not familiar with the terms used or may not be paying attention.  That having been said, it seems pretty obvious the OP did install the Mint bootloader to the MBR and deleting the Mint partition resulted in the problem because almost all the Grub files are on the partition.

---

### Post by jsleotti on 2015-11-01
Yes, I understand what happened now. When I wiped out my Windows install it wasn't an issue; I didn't know that installing Mint would wipe out the bootloader from Ubuntu. It was a relatively simple mistake I can be sure won't be a problem again!

---

