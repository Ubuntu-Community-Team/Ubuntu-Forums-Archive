---
title: "Freeze / Memory Leak"
date: 2006-12-17
forum: General Help
---

### Post by jeffkny on 2006-12-17
Hi. I am new to Ubuntu, but not new to Linux (RHEL user for many years). I have had issues of my system freezing, or being unresponsive, and have to power off. System is an IBM Thinkcentre, 160Gb HD, 1Gb memory. I have the System Monitor running, a habit since running RHEL. It shows right now 0% Processor, 21% Mem used by Programs, 57% used as cache. So, is there a way to clear the cache from memory without rebooting? Just logging out does not clear this. I don't think my system is using the swap, or at least I never seem to notice swapping.For the record, I love Ubuntu, very user friendly. This morning my Volume control burped, and rebooting does not bring it back, only an error that the panel encounter a problem: OAFIID:GNOME_MixerApplet. 

Thanks
Jeff K

---

### Post by jeffkny on 2006-12-17
Additional text for above issue: When booting up, first error I get is this: 

There was an error starting the GNOME Settings Daemon.
Some things, such as themes, sounds, or background settings may not work correctly.
The last error message was:
Process /usr/lib/control-center/gnome-settings-daemon exited with status 127.

Can I fix this with a config file or update? Thanks 

Jeff K

---

### Post by merovingian on 2007-01-03
add **noapic nolapic** to your kernel boot options

eg.
edit /boot/grub/menu.lst


kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hda1 ro quiet splash vga=794 noapic nolapic


Should work, it worked great on my ThinkCentre.

Alex

---

