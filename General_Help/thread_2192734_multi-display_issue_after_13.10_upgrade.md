---
title: "multi-display issue after 13.10 upgrade"
date: 2013-12-09
forum: General Help
---

### Post by gamblor01 on 2013-12-09
I upgraded last week to 13.10 and have had problems with my external monitor configuration ever since.  I am running this on a Macbook pro 9,1 with the Intel driver (no nvidia driver installed and I don't think that using the 650M is even possible without vga_switcheroo, which I'm not using).

With the external monitor attached, both displays work fine.  However, if I want to disconnect and move my laptop I have two options:

1. disconnect the cable
2. launch the "Displays" app from the dash, select the external monitor, slide it to OFF, and click Apply


When using 13.04 I used the latter option and it would properly move all of the running apps back to my laptop's display and everything worked fine.  As soon as I returned to my desk I would just connect the monitor again, enable it in displays, and move windows back over as needed.  However, if I turn off the external monitor in 13.10 then not only does it go blank, but so does my laptop screen.  There seems to be no way to recover other than hold the power button down and reboot.  I did get it to respond once to a virtual terminal (CTRL+ALT+F1) but typically it seems that I cannot even get there.

If I disconnect the cable then the laptop display continues to function, but any programs that were open on the external display are impossible to access.  I have to either move them all over to the laptop display BEFORE disconnecting the cable, or disconnect and then kill/restart each PID.

What is the best way to troubleshoot this?  I assume that I should cause the failing scenario and then SSH into the box and retrieve some logs?  If so, which logs?

---

### Post by raziv on 2013-12-12
Similar problem here.

---

### Post by gamblor01 on 2013-12-13
I'll have to search some bug reports and see if anyone else has already reported this.  I have unfortunately noticed that even if I simply move all open windows to my laptop screen and then disconnect the external monitor, the laptop's X display seems to just lock up and can no longer be used.  I will need to do further testing to see exactly what triggers it, but I think that it works until the display goes to sleep.  After that, it won't wake back up to function properly.

Out of curiosity raziv, are you also running on a Macbook Pro?  I remember reading this page [http://linux-hybrid-graphics.blogspot.com/2012/04/apple-macbook-pro-and-linux-hybrid_21.html](http://linux-hybrid-graphics.blogspot.com/2012/04/apple-macbook-pro-and-linux-hybrid_21.html)

which says that Apple uses a physical mux to switch between graphics cards (implying that other laptops don't).  Perhaps it is something related to the video driver on a Macbook?


> 
[FONT=Arial]Apple implemented the switching of the two graphic cards using a[/FONT]
[FONT=Arial]"chip" dubbed the "gmux". This gmux can power down the dedicated[/FONT]
[FONT=Arial]graphics card, switch the DDC, internal and external display[/FONT]
[FONT=Arial]connections individually between both cards and then set the backlight[/FONT]
[FONT=Arial]brightness. Unlike most newer laptops with hybrid graphics, Apple's[/FONT]
[FONT=Arial]Macbook Pros still use a physical mux.
[/FONT]

---

### Post by raziv on 2013-12-14
I'm running on Acer Aspire One D150, gamblor01, and according to lshw it has an Intel 945GSE graphics card. I'm not an expert, but I think it means it is not an integrated one. The driver in use is i915.

---

### Post by gamblor01 on 2013-12-14
Ok so you just have a single card and it's still happening.  It could be something with the Intel driver I suppose.  I guess we should just open a bug report and see where it goes.  It's always a pain to get the correct package specified.  I'll see if I can get some further logs of some sort and open a bug report.  I'll post the link here when I do.  I'm quite busy this weekend so it may take me a few days.  Thanks for the info.

---

### Post by jeffreykutcher on 2013-12-14
Similar issue:

Linux 3.8.0-34-generic #49~precise1-Ubuntu SMP Wed Nov 13 18:05:00 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

          product: AMD Phenom(tm) II X4 965 Processor
          vendor: Hynix Semiconductor (Hyundai Electronics)

With two monitors, one a Dell 20" DB9, second Samsung HDMI, right mouse clicking on the desktop and choosing Change Desktop Background, the window appears on the second display, not the first. Turns out this is true for many other applciations such as networking, system monitor, calculator and the list goes on. To view application on second monitor if second monitor is not on, click the Workspace Switcher and drag the application to the first monitor.

---

