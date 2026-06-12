---
title: "Is my CPU temp incorrect?"
date: 2007-06-25
forum: General Help
---

### Post by MadTxn on 2007-06-25
Greetings.  I have an HP dv8000t (specs below) that keeps "overheating".  I have the Gnome temperature applet, and it shows one core at 27C (always) and one varying from 43C-82C (where it shuts down).  I have a suspicion that those temps aren't right, and it's shutting me down unnecessarily.  Is there anything else I can do to troubleshoot/check the temp in a different way?  I can make it happen almost at will by viewing something in flash in firefox.  TIA

# Genuine Windows XP Professional (uh... no.  Ubuntu Feisty)
# Intel(R) Core(TM) Duo processor T2250 (1.73 GHz)
# 17.0" WSXGA+ BrightView Widescreen (1680x1050)
# 256MB NVIDIA(R) GeForce(R) Go 7600
# 2.0GB DDR2 SDRAM (2x1024MB)
# 100 GB 5400 RPM SATA Hard Drive
# LightScribe Super Multi 8X DVD+/-RW w/Double Layer
# Intel(R) PRO/Wireless 3945ABG Network w/Bluetooth

---

### Post by EXCiD3 on 2007-06-25
Have you noticed much heat coming from your laptop?

---

### Post by floke on 2007-06-25
You can check the temp with (from terminal)

acpi -t

or watch it with

watch acpi -V

---

### Post by MadTxn on 2007-06-26
A *lot* of heat?  no.  As for the acpi command, it reports the same temp as the gnome applet, but it seems odd to me that both cores can be going full out, and one temp changes and the other stays at 27C.  Shouldn't both change?  Or maybe it's measuring something else?

---

### Post by jm2003uk on 2007-06-26
Have a look in your BIOS and see if there's a hardware monitoring section. This will normally provide you with temperatures and fan speeds, as well as what temperature to shutdown at (usually). This will be independent of any OS you use and is pretty much a failsafe which will just cut the power if that temperature is reached. Happened on my pc a few times because i had it set a bit low.

---

### Post by floke on 2007-06-26
You could also try manually disabling one of the cores in the bios and see what happens to the temperature.

---

### Post by MadTxn on 2007-06-27
Well, my BIOS has neither option, so I'm going to try to upgrade.  However, HP (as far as I can see right now) requires Windows to update the BIOS, so I'm going to try to create a windows live CD to update, because I doubt it will work through VMWare.

---

### Post by gpap on 2007-06-27
MadTxn, I have the same problem on a much more modest laptop but I think the following applies any machine. Are you aware of bug [[COLOR="Red"]22336[/COLOR]]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/22336") ? People report that ```
acpi=off noacpi
``` in the boot options of grub normally works but it's quite radical (my usb ports don't work and I need to switch off manually). There's (many) more proposed solutions in the bug report-hope one works for you. Was this behaviour by any chance triggered by installing new software? Mine started failing me after I installed a win xp driver for a wireless card with ndiswrapper.

---

