---
title: "X-Server won't start, can't get in Ubuntu"
date: 2007-06-09
forum: General Help
---

### Post by Wokm4n on 2007-06-09
Hey

After I installed ubuntustudio I tried to boot the lowlatency kernel. The X-server couldn't be started and I got this output:

[INDENT]FATAL: Error running install command for nvidia
(EE)NVIDIA (0): Failed to load the NVIDIA kernel module!
(EE)NVIDIA (0): *** Aborting ***
(EE)Screen(s) found, but none have a usable configuration

Fatal server error:
no screens found[/INDENT]

So I tried to update the drivers of my Geforce5200 with envy. Allright everything went well and I rebooted. I still couldn't get into the lowlatency kernel! So I wanted to just boot the normal kernel but X wouldnt load there either!

[INDENT]Failed to initialize the NVIDIA kernel module!
Please ensure that there is a supported NVIDIA GPU in this system[/INDENT]
.....

So I'm on XP again.. I really don't know what to do, I hope someone could help me :(

---

### Post by conjur3r on 2007-06-09
If you've successfully reinstalled the nvidia drivers and it still doesn't work, then try resetting the xorg (xserver) configuration with:

# dpkg-reconfigure xserver-xorg

This should bring you back to a non-accelerated desktop.

---

