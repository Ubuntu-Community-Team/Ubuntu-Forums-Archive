---
title: "Takes long time to boot and display login screen"
date: 2007-02-25
forum: General Help
---

### Post by smanandhar on 2007-02-25
I installed Ubuntu 6.10 in my computer with Intel pentium 4 1.7 Ghz Cpu and 384 mb of ram. My motherboard is intel 845 glly and 15'' monitor.
Installation went fine, but every time i boot my computer with ubuntu, it takes very long time to boot and to display login screen. After boot it works fine.

What could have been wrong with my ubuntu??

---

### Post by tgalati4 on 2007-02-25
Welcome to the community.

In a shell:

dmesg            (look for interesting things going on)

Look in /var/log, especially xorg.0.log for errors and other interesting tidbits that may give a clue to slow startup.  I have a 2.8 GHz machine and it still takes 2 minutes to boot.  But I only have to reboot once every 3 to 6 months so I don't care.

---

### Post by dcstar on 2007-02-25
> **smanandhar said:**
> I installed Ubuntu 6.10 in my computer with Intel pentium 4 1.7 Ghz Cpu and 384 mb of ram. My motherboard is intel 845 glly and 15'' monitor.
Installation went fine, but every time i boot my computer with ubuntu, it takes very long time to boot and to display login screen. After boot it works fine.

What could have been wrong with my ubuntu??

Network issues can also cause these sort of problems, if your DNS and/or hostname setup is wrong, there can be delays.

Also do a forum search for "disable ipv6".

---

### Post by bmathis on 2007-02-25
update your BIOS... I had the same problem and fixed it that way. I have no idea why it fixed it but it did.

---

