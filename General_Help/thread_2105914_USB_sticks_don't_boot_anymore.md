---
title: "USB sticks don't boot anymore"
date: 2013-01-17
forum: General Help
---

### Post by Snapcase on 2013-01-17
I'm currently testing different audio dedicated distros installed in USB stick drives, but for some reason they don't boot anymore. I've checked the BIOS settings and "External USB" is set as primary in booting priority as it should. But none of the sticks boots. I guess this is some kind of issue related with Grub. It's a triple boot Kubuntu 12.10, Mac OS X 10.6 and Win XP PC. They all boot fine. But the sticks stopped booting. I have to disconnect the internal disks in order to run them.

I have no idea about how to tweak Grub. Any help will be welcome. Thanks in advance.

---

### Post by ajgreeny on 2013-01-17
You often need to press a key (F12, F2) at power-on to change the boot order on machines.  Check in the mb info if that's the case here.

---

### Post by Snapcase on 2013-01-17
None of those keys made an effect. With mb do you mean the Bios?

---

### Post by ajgreeny on 2013-01-17
> **Snapcase said:**
> None of those keys made an effect. With mb do you mean the Bios?
Yes, I do mean the BIOS, but that is usually in the mb info.
You masy also see something flash up on screen, eg "Press F2 to change boot device" but you need to look carefully as it is gone in a second or less.

---

### Post by iowabeakster on 2013-01-17
I had a similar problem.

What I found is that if I want to boot from a USB thumb drive, my computer needs to be powered down for maybe 30 seconds.  If I quickly restart it (or restart from some other OS) it goes directly to hard drive boot (even with USB first choice on the BIOS list).

It took me quite a while to figure out why I could get it to boot from USB sometimes but not all the time.  Since I've been letting it sit for while before reboot (from a USB), it does it every time.

Hopefully it works for you.  Good luck.

---

### Post by Snapcase on 2013-01-17
Solved!!!

I left it powered off for a few minutes. Nothing changed. Then rebooted several times looking for that elusive instant message. Didn't saw anything either... so I went back to the Bios and found that there are two different menus for the booting priorities!!! :confused:

I've never saw a setup like this before and indeed I've never went inside that second menu. But I selected again the USB stick as first booting device there in that second menu and now it boots fine. This MoBo has life on it's own, but now I know how to put this crazy horse it back in the stables. 

Thanks so much for the tips!

---

