---
title: "failed to install 24.04 timed out waiting for udev queue to empty"
date: 2024-04-28
forum: General Help
---

### Post by Unguidedone on 2024-04-28
the installer hangs on first install, it will spin and spin, if you press esc you can look at the diagnostics 

failed to install 24.04 timed out waiting for udev queue to empty
systemd[1] failed to fork off sandboxing environment for executing generator: protocol error 
systemd[1] freezing execution 
[!!!!!!!!] failed to start up manger



intel rst is disabled and in non raid configuration
secure boot is disabled - i tested it for 22.04 it did not boot with it enabled but did boot with it disabled'
csm also works for 20.04 uefi also works for this install none is working for 24.04

if secure boot is enabled or disabled same error
if running in csm mode same error
if running in uefi mode same error
rst mode is disabled


i loaded up 24.04 in virtual box and that install also failed, i got a black screen with a x pointer


the motherboard is a msi pro z690-a ddr4 with 96 gb ram and a i9-12000

when im installing where can i drop into shell, i want to run lsusb to detect if the installer sees the hardware (870 evo 2.5 sata 4 tb ssd)

what am i doing wrong how can i trouble shoot this

---

### Post by Unguidedone on 2024-04-28
I was able to get the installer working for 22.04, it took about 30 minutes of that ball spinning to get to the install screen.  so far with the same motherboard configs 24.04 is not working.

---

### Post by Unguidedone on 2024-04-28
alright so i pulled the drive out of the main computer and swapped it into another, the installer failed so i put it into safe graphics and it installed in about 10 min total time all good.  so i pulled the drive out and replaced it back into main computer and after crypto setup on boot it gave the error:

systemd[1] failed to fork off sandboxing environment for executing generator: protocol error 
systemd[1] freezing execution 
[!!!!!!!!] failed to start up manger

its some motherboard setting that is breaking it.  anyone have any idea??


i can install 20.04 - the installer pops up instantly, 22.04 instant pop up install prompt.  even if the os is loaded to another computer you cant load it or install it.

---

### Post by youssefeldakar on 2024-06-26
I've just run into a similar situation attempting to install 24.04 on an old machine with an Adaptec RAID controller (aacraid kernel module).

Thank you for any pointers to follow.

---

### Post by currentshaft on 2024-06-26
How are you creating the USB installer?

---

