---
title: "Help Killed My Ubuntu 13.04, my computer is dead."
date: 2013-06-29
forum: General Help
---

### Post by ernestj on 2013-06-29
My battery died on the computer shut down. Now I can not get it to reboot.

I get the following:

mount: mounting /dev on/root/dev failed: No such file or directory 

(initramfs) [I]blinking curser


[/I]Help!!!!

Thanks,
Ernie

---

### Post by Mark Phelps on 2013-06-29
We're not mind readers here -- is this a laptop?  Some laptops, unfortunately, will NOT boot without a working battery.  Without telling us the make and model PC, you're forcing us to guess -- which will do you no good.

---

### Post by grahammechanical on 2013-06-29
I have not tried this so I do not know if it will work but at the grub menu go to Advanced Options and select Recovery Mode and at the menu select Grub  -  Update Grub boot loader. That may not work because some part of Linux needs to load before we see that screen.

You should also think about using a live session to backup your data and then re-installing. That might be the easiest way.

Regards.

---

### Post by ernestj on 2013-06-29
Sorry. this is a laptop. Asus U56.

tried Elemetary USB and could not access the drive.

I believe it said unable to mount drive.

I can access the purple screen (grub) and can choose advance session.

When I choose recovery mode. I get the same response from the first post.

Thanks,
Ernie

---

### Post by Bashing-om on 2013-06-29
ernestj; Hi !

Before delving deeper, try this:
Boot the liveUSB (bios is set to usb as 1st boot priority); At the purple splash screen depress the shift key -> language scrren, press the escape key to accept the default -> Boot options screen:
In this boot options screen is the option "boot from hard drive"....
Does selecting this option boot into your installed system ?
Yes = one thing
No = do something else.

[INDENT][INDENT]it is all in the process[/INDENT][/INDENT]

---

### Post by ajgreeny on 2013-06-29
A similar thing happened to me on a desktop machine when we had a power failure.

I booted to a live system and ran ```
sudo e2fsck /dev/sda1
``` then the same for sda2 which were my two ubuntu partitions, root, sda1, and /home, sda2.  That found and repaired some problems and afterwards the installed system booted fine.

---

### Post by ernestj on 2013-06-29
> **ajgreeny said:**
> A similar thing happened to me on a desktop machine when we had a power failure.

I booted to a live system and ran ```
sudo e2fsck /dev/sda1
``` then the same for sda2 which were my two ubuntu partitions, root, sda1, and /home, sda2.  That found and repaired some problems and afterwards the installed system booted fine.







It worked!!!!!
Thank you!!!!!!!!!!!!!!!!! 
Solved!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

---

