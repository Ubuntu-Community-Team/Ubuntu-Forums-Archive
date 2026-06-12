---
title: "Problems Booting"
date: 2013-02-26
forum: General Help
---

### Post by Kizipotamus on 2013-02-26
Short: When I boot up, I am met with a purple screen (no Grub). I reboot, and after passing Grub, I will be met with a black screen with a blinking underscore. This will be what I encounter 2 - 30 times before I can actually get into the OS. 

Long: I installed 12.10, and this was what happened. I tried to install 12.04 instead, to see if that solved the problem, but I couldn't even get it to install. Next I tried installing 13.04, which went smoothly, but I'm again encountering this same bootup issue as I had with 12.10. It's pretty frustrating to take 20+ minutes of rebooting my computer to actually get to use it, and I can't find anything that helps. 

Also, 13.04 seems to be incapable of making a bootable USB that works. I've used countless ISOs, and both Startup Disk Creator, and Unetbootin, to no avail. Booting from the USBs gives me a "Non System Disk" message. This means I can't even try installing a different OS.

---

### Post by Bashing-om on 2013-02-26
Kizipotamus; Hi ! Welcome to the forum.

Most likely a graphics driver issue; Try this:
Boot up ubuntu; soon as the bios screen clears, depress and hold the shift key ->grub menu; select "recovery mode" kernel -> recovery console -> "resume normal boot" ->GUI login; Login -> desktop (degraded graphics OK):
12.04 version: launcher (left side of screen) -> System Settings -> Additional Drivers -> install the recommended driver.
12.10 version: Launcher-> Ubuntu Software Center ->Software Sources (task bar menu) -> Addition Drivers (tab) -> install recommended driver.
13.04 version //unable to advise//
[INDENT][INDENT]just try'n to help

[/INDENT][/INDENT]

---

### Post by Mark Phelps on 2013-02-26
V13.04 is still in Alpha development.  You shouldn't be using it unless you are highly experienced in Ubuntu and easily able to fix your own problems -- as alphas are known to have problems.

If you want help on 13.04, you need to post to the Ringtail Development forum section, not here.

---

### Post by Kizipotamus on 2013-02-26
> **Mark Phelps said:**
> V13.04 is still in Alpha development.  You shouldn't be using it unless you are highly experienced in Ubuntu and easily able to fix your own problems -- as alphas are known to have problems.

If you want help on 13.04, you need to post to the Ringtail Development forum section, not here.

Sorry, but you didn't read my post very well. I'm having the same problems on 12.04, 12.10, and 13.04. Actually, 13.04 is working the best so far.


> **Bashing-om said:**
> Kizipotamus; Hi ! Welcome to the forum.

Most likely a graphics driver issue; Try this:
Boot up ubuntu; soon as the bios screen clears, depress and hold the shift key ->grub menu; select "recovery mode" kernel -> recovery console -> "resume normal boot" ->GUI login; Login -> desktop (degraded graphics OK):
12.04 version: launcher (left side of screen) -> System Settings -> Additional Drivers -> install the recommended driver.
12.10 version: Launcher-> Ubuntu Software Center ->Software Sources (task bar menu) -> Addition Drivers (tab) -> install recommended driver.
13.04 version //unable to advise//
[INDENT][INDENT]just try'n to help

[/INDENT][/INDENT]

I've installed the drivers but the only ones that work for me at all are the preinstalled open source ones.

---

### Post by Bashing-om on 2013-02-27
Kizipotamus; 

Lets look at the hardware and driver to see what can be done.

Post the out put of terminal codes:
```
lspci | grep VGA
lspci -nnk | grep -iA3 vga
```[INDENT]try'n to help

[/INDENT]

---

