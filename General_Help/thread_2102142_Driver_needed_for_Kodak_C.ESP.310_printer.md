---
title: "Driver needed for Kodak C.ESP.310 printer"
date: 2013-01-06
forum: General Help
---

### Post by mawil1013 on 2013-01-06
I'm running 10LTS, Been trying to get correct driver for my, 
Kodak C ESP 310 printer.

The search won't bring the specific drivers, they don't work.

I can say that U12.1 does find the specific driver and it will connect through wifi and does print the test page. But, this laptop will not run 12.1. The screen has no back light when running 12.1.

Running ubuntu 10LTS, on my Acer Aspire 5336-2524, everything runs, the screen, the wifi, etc, If I can get the correct driver for my Kodak printer all will be fine.

PS: if you have the same laptop and have a sure fire way to get ubuntu 12.1 running, as in, the screen works, I would also be interested in that. I already know that by attaching a monitor to the laptop will work when running u12.1 on this Acer Aspire 5336-2524, but is not practical. ubuntu 12.1 runs much better than 10LTS on this laptop except the screen backlight simply won't work. Sob! one thing or the other!

---

### Post by Pjotr123 on 2013-01-06
I just installed Xubuntu 12.04.1 on an Acer Aspire 5336, running on the latest BIOS (1.14). With backlight problem.... And I was able to solve it. This solution will probably work on 12.10 as well, so that your Kodak printer problem will be solved, too.

There are many how-to's on the web for the backlight problem on this machine, and they are twofold:
1. Add some boot options to Grub;
2. Or add a line to /etc/rc.local.

Only number 2 gave me a solid solution, so I'll give you number 2:

- boot in Recovery Mode and choose Resume. This will give you a "normal" display with only a wrong resolution.

- Now the real thing:
First install Leafpad.
In the terminal:
```
sudo apt-get install leafpad
```

Then:
```
gksudo leafpad /etc/rc.local
```

Add this line, just above the line "exit 0":
```
setpci -s 00:02.0 F4.B=01
```

Explanation: the BIOS is completely messed up by Acer, so that controls are reversed.... Normally maximal brightness would not be 01, but 100!

Save the file and reboot normally.

Note: disable suspend and all other (power)features that blank the screen, because they will result in a black screen again...
[https://sites.google.com/site/easylinuxtipsproject/bugs#TOC-Hibernate-and-suspend-don-t-always-work-well:-they-make-some-computers-malfunction-or-even-enter-a-coma](https://sites.google.com/site/easylinuxtipsproject/bugs#TOC-Hibernate-and-suspend-don-t-always-work-well:-they-make-some-computers-malfunction-or-even-enter-a-coma)
(item 7)

Note 2: you might have better results with boot options for Grub, so to be complete: [http://ubuntuforums.org/showthread.php?t=2028684](http://ubuntuforums.org/showthread.php?t=2028684)

Good luck! :)

---

### Post by fyfe54 on 2013-01-06
Try this.  [http://ubuntuforums.org/showthread.php?t=1963303](http://ubuntuforums.org/showthread.php?t=1963303)

Worked for me.

---

### Post by paulnewall on 2013-01-06
Get the c2esp driver from
[http://sourceforge.net/projects/cupsdriverkodak/files](http://sourceforge.net/projects/cupsdriverkodak/files)
I think with 10LTS you could download and install this deb package
[c2esp_25c-1_i386.deb]("http://sourceforge.net/projects/cupsdriverkodak/files/c2esp_25c-1_i386.deb/download")
With the latest ubuntu you should download the latest source code version of c2esp. Compile and install it following the instructions in the README and INSTALL files.

---

