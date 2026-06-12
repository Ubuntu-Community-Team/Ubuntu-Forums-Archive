---
title: "PC does not shut down"
date: 2013-02-18
forum: General Help
---

### Post by raunhar on 2013-02-18
Ubuntu Version 11.10
Desktop

When I try to shut down the PC, it shows the text:
*Killing all renaming process   Status Failed
150.538963 System halted.
And the PC hangs.

This problem started after the recent updates.
I tried starting the PC in recovery mode for any broken packages, but it did not show any.

If the text does not come, the closing Ubuntu windows stops at last two points.

It is a dual boot, so I have to restart the PC in windows and shut it down.

---

### Post by albandy on 2013-02-18
> **raunhar said:**
> Ubuntu Version 11.10
Desktop

When I try to shut down the PC, it shows the text:
*Killing all renaming process   Status Failed
150.538963 System halted.
And the PC hangs.

This problem started after the recent updates.
I tried starting the PC in recovery mode for any broken packages, but it did not show any.

If the text does not come, the closing Ubuntu windows stops at last two points.

It is a dual boot, so I have to restart the PC in windows and shut it down.

Is your graphic card from nvidia?

---

### Post by fuorviatos on 2013-02-18
> **raunhar said:**
> Ubuntu Version 11.10
Desktop

When I try to shut down the PC, it shows the text:
*Killing all renaming process   Status Failed
150.538963 System halted.
And the PC hangs.

This problem started after the recent updates.
I tried starting the PC in recovery mode for any broken packages, but it did not show any.

If the text does not come, the closing Ubuntu windows stops at last two points.

It is a dual boot, so I have to restart the PC in windows and shut it down.
Can you show us the output of >  lspci | grep -i VGA  so we know what video card you've got?

---

### Post by wildmanne39 on 2013-02-18
*Thread moved to **General Help**.*

---

### Post by raunhar on 2013-02-19
The graphic card is not from nvidia. It is the default on-board card.

---

### Post by albandy on 2013-02-19
> **raunhar said:**
> The graphic card is not from nvidia. It is the default on-board card.

Edit the file /etc/default/grub:
sudo gedit /etc/default/grub

then change that line:
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
to this:
GRUB_CMDLINE_LINUX_DEFAULT="acpi=force quiet splash"

save the changes and type:
sudo update-grub
then reboot 

And test if the computer can shut down.

---

### Post by raunhar on 2013-02-19
Same problem persists even after editing the grub file.

---

### Post by dino99 on 2013-02-19
to get the verbose mode (letting you know what happen while shutting down), remove the "quiet splash" from /etc/default/grub

then : sudo update-grub

also clean the system as much as possible: 
clean/autoclean/autoremove/gtkorphan/bleachbit (as root, but carefully set the options)

and of course, glance at .xsession-errors & /var/log/dmesg to find possible usefull errors.

---

### Post by albandy on 2013-02-19
> **raunhar said:**
> Same problem persists even after editing the grub file.

type this:
dmesg > log.txt
then upload the file log.txt

---

