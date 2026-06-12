---
title: "[SOLVED] Trouble Installing"
date: 2008-03-01
forum: General Help
---

### Post by wide-load on 2008-03-01
I ran Unbutu Live om a 667 mhz Celeron and it worked Ok.  So I installed it to my hard drive.  It worked OK.  However it found about 196 updates, which it downloaded and installed.  After that when I try to boot it, it goes through the process, until the desktop is ready to come up.  When it does I get a bunch of wavy lines on my monitor, like a TV that is on a channel with no broadcast..  From the colors I think it is a normal desktop.

I think this is a matter of my screen resolution or display rate being wrong, but since Ubuntu is brand new to me I am clueless as to how to resolve it.

HELP!!!!!!!:mad:

---

### Post by wide-load on 2008-03-01
I probably should have mentioned I'm running version 7.10

---

### Post by forestpixie on 2008-03-01
try reconfiguring x

start in recovery mode

dpkg-reconfigure -phigh xserver-xorg

---

### Post by wide-load on 2008-03-10
Thanks for your help.  That resolved it.  Although I got some "screwy" message that said "FATAL:  Error inserting batery (lib/modules/2.6.22-14-generic kernal/drivers/acpi/battery.ko).  Because of the error message I didn't think it was working.  However when I rebooted the graphics came up OK.

Any idea what is behind that error message?

---

### Post by forestpixie on 2008-03-11
no afraid not - can you mark thread solved now that it is :)

---

