---
title: "cannot get ubuntu to install on sata drives"
date: 2007-11-24
forum: General Help
---

### Post by BradDollar on 2007-11-24
first off, i'm a total linux noob, i'm trying to get ubuntu 7.10 on my second box. live cd boots fine and install goes off without a hitch. if i install to my near death IDE drive it works fine and it boots up to the desktop after install, but if i install it to either of my new SATA drives, it doesn't boot to the desktop after install. it gives me the ubuntu loading screen, but after ~5 minutes it drops me out to 'busy box v1.1.3' and gives me a prompt with '(initramfs)' and i can't figure out how to accomplish anything from there.

somebody in IRC had me hit F6 at the live cd menu and add 'noapic', but after installing again i still cannot get to the desktop.

can anybody gimme a hand?

my apologies if there is another post on this, but i couldn't find anything.

thanks
-brad

---

### Post by p_quarles on 2007-11-24
If I understand correctly, you have an IDE drive, and at least two SATA drives on this same computer, right?

Linux support for SATA is actually really good, so my guess is that the problem has something to do with where the boot file is located rather than with the type of drive you're using. If the IDE drive is the master, that *could* explain the situation. 

I can offer a few possible solutions, but I'm nowhere near enough of an expert to guarantee they'll work. 

1) If, as you say, the IDE drive is "near death," you could just remove it and then install Ubuntu on one of the SATA drives.

2) When you get the command prompt, run this command:
```
startx
```
3) If that doesn't work, run this command (assuming you're running Gnome, the default Ubuntu desktop):
```
sudo /etc/init.d/gdm restart
```
4) If #3 fails to do anything, I would recommend the "Alternate" disk. This will allow you install the system, and then come back here and get help with setting up your video card's driver.

---

### Post by BradDollar on 2007-11-25
thanks for the help.

yes, physically there is 1 IDE drive and 2 SATA drives. the IDE drive has remained unplugged with the only exception being that i hooked it back up to see if i could get ubuntu working on it, and it did. i've tried the install a few times on the SATA drives since then so i don't believe the problem has anything to with the IDE drive. the SATA drives are running indepently and not in a raid config.

when i try #2 or #3 at this '(initramfs)' prompt i just get '/bin/sh: startx: not found' or /bin/sh: 'sudo: not found'.

i'll give the alternate disk a try tomorrow.

-brad

---

### Post by sandysandy on 2007-11-25
> **BradDollar said:**
> thanks for the help.

yes, physically there is 1 IDE drive and 2 SATA drives. the IDE drive has remained unplugged with the only exception being that i hooked it back up to see if i could get ubuntu working on it, and it did. i've tried the install a few times on the SATA drives since then so i don't believe the problem has anything to with the IDE drive. the SATA drives are running indepently and not in a raid config.

when i try #2 or #3 at this '(initramfs)' prompt i just get '/bin/sh: startx: not found' or /bin/sh: 'sudo: not found'.

i'll give the alternate disk a try tomorrow.

-brad

hi 

i have faced quite a few problems in installing ubuntu myself, but these were related to the IDE drive.

what are ur system specs. also post output of sudo fdisk -lu

regards

---

