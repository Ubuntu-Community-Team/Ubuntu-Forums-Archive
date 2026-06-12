---
title: "notebook fan comes on briefly every 15 seconds on XPS-15 9570"
date: 2018-09-23
forum: General Help
---

### Post by ivo-welch on 2018-09-23
I managed to install ubuntu 18.04.1 on an XPS-15 9570.  as far as I can tell, it runs solid and everything is working.  (I do not have or use a fingerprint reader.)  this is due to the great work by [https://github.com/JackHack96/dell-xps-9570-ubuntu-respin](https://github.com/JackHack96/dell-xps-9570-ubuntu-respin) .

my typical load while idle is around 0.3.  alas, about every 10-15 seconds, my idle silent notebook spins up the fans for 3-4 seconds while on power.  this is very annoying.  I would rather have it always be on just a little, or take higher base temperatures.

I have installed Freon (lmsensors), but while it nicely tells me my temperatures, it does not seem to have options to change fan behavior.

I have tried different power profiles through the CPU power manager (Gnome), but the on-off remains.

how does one change this behavior?  it's driving me crazy.

---

### Post by idkwhatimdoing1.0 on 2018-09-25
typically with Dell XPS series you can change the fan setting over in the BIOS so just press either esc or or delete or F2 when you open up the laptop and select interupt startup or BIOS setting and find fan speeds. Usually the settings are to always turn on fans when plugged in power, turn on fans at last second kind of thing. See if any of the options seem to help.

---

### Post by ivo-welch on 2018-09-26
I looked, but there does not seem to be such an option in the XPS 9570 BIOS.

---

### Post by idkwhatimdoing1.0 on 2018-09-27
That's alright I have another option. In Linux there is a program named TLP it is meant to monitor and prevent CPU overheating by turning on the fan and what not. Therefore maybe by installing this program it could get rid of the annoying fan coming in every 15 seconds as the program would only turn it on if needed. So maybe you can try this. Open up terminal and enter these lines.
```
sudo add-apt-repository ppa:linrunner/tlp
apt-get update
apt-get install tlp tlp-rdw
tlp start 
```
You may need to restart your system before doing TLP start. This should technically work.

If you are unhappy with TLP or it just simply doesn't work you can remove it by typing this line of code in the terminal

```
[COLOR=#242729][FONT=Consolas]sudo apt-get --purge remove tlp[/FONT][/COLOR]
```

Best of luck!

---

