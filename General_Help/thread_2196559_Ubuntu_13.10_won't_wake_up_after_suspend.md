---
title: "Ubuntu 13.10 won't wake up after suspend"
date: 2013-12-30
forum: General Help
---

### Post by irac1987 on 2013-12-30
[COLOR=#333333][FONT=UbuntuRegular]I have some difficulties with Ubuntu 13.10 (3.11.0-14-generic) and waking up from suspend state. Screen just goes blank, and there is some kind of prompt blink in upper right corner after I just need to restart my computer.[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]Specs:
 
DE: Gnome 
Intel® Core™ i7-3770 CPU @ 3.40GHz
 GeForce GTX 650/PCIe/SSE2 with: NVIDIA binary Xorg driver, nvidia-331 (open source)
16 GB of RAM
 (/ folder on SSD Drive, /home on HDD)[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]P.S. Nvidia graphic driver works perfectly without any glitches. Thanks for any help you can provide..[/FONT][/COLOR]

---

### Post by Kirboosy on 2013-12-30
Welcome to the forums! :D

> [COLOR=#333333][FONT=UbuntuRegular]  GeForce GTX 650/PCIe/SSE2 with: NVIDIA binary Xorg driver, nvidia-331 (open source)[/FONT][/COLOR]

When you say you have the opensource drivers installed do you mean the nouveau drivers? From what I have gathered people are saying installing the official Nvidia drivers fix the problem.


Hope that helps!
~Caboose

---

### Post by egeezer on 2013-12-30
If it isn't a graphics problem, it may have to do with the power manager.  Try in the terminal using

```
sudo pm-suspend
```

That might suspend properly (it does better for me than suspending via the GUI).

---

### Post by irac1987 on 2014-01-01
It is proprietary driver directly installed from nvidia site.

---

