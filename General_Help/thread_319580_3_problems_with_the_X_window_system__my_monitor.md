---
title: "3 problems with the X window system / my monitor"
date: 2006-12-15
forum: General Help
---

### Post by Portable_Jim on 2006-12-15
Dapper, Gnome and a digital (brand name)[FONT=Nimbus Mono L][FONT=Verdana]PCXBV-PH[/FONT] [/FONT]monitor.
Rest of system specs [here]("http://portablejim.awardspace.com/system_info.html")

No problems under windows.

Problem #1: Computer locks up ad throws up light blue bars separated by a black strip. The network still has power and our family's router still says that the computer is connected and has an IP address. No hard drive activity, and the download I was doing stopped. The computer gave no response to any key presses or mouse movements.

Problem #2: Monitor randomly turns off. Computer still runs with monitor off - still responds (eg, can open terminal but not shutdown - I couldn't really see what I was doing). Has happened several times. It seems to be fixed, but source of problem is still unknown.

Problem #3: Screen scrambles, like the refresh rate is too high / resolution too large. Has only occurred once.

All three of these problems happen without any warning meaning that what I am working on (past my last save point) is lost because I have to reboot the computer.

Please help me diagnose the source of the problems and find solutions to them.

---

### Post by taurus on 2006-12-15
Boot into recovery mode from GRUB menu and perhaps reconfigure your X again with

```
dpkg-reconfigure xserver-xorg
```

---

### Post by Portable_Jim on 2006-12-16
> **taurus said:**
> Boot into recovery mode from GRUB menu and perhaps reconfigure your X again with

```
dpkg-reconfigure xserver-xorg
```
Have already done that. Did not fix problems.

Problem #2 happened again. Symptoms: 
--100% CPU usage for a while, then clicking to open system monitor.
was able to turn off into maintenance mode, then the screen comes back on, so I can shutdown the box properly.

I have the same settings (I think) as windows, but Windows never turned the screen off on me.

---

