---
title: "Low resolution after installation"
date: 2016-02-03
forum: General Help
---

### Post by mirobelix on 2016-02-03
Hi,
I tried a live system of Lubuntu 15.10 on my very old notebook.
It worked fine so I decided to install it.
But after the installation, only about a third of the screen is used. The rest is black and I can't changed the resolution to a higher value.
Since the live system works fine, I'd like to copy the settings/driver it uses to the installation.
In the live system I typed 
lspci | grep VGA
and got
VGA compatible controller: Intel corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 03)

The graphics settings are stored in xorg.conf.d, as far as I understand.
In an online HowTo I found that it can be found in /usr/lib/X11/, but in my live system I didn't find it there.
I found a similar directory at /usr/shared/X11/, but there doesn't seem to be a config file for the monitor.

My question is, how can I copy the settings of the live system to my installation ?

Thanks in advance.

---

### Post by mörgæs on 2016-02-04
Hi, welcome to the fora.

For old Intel graphics I recommend UXA acceleration. If you click the link in my signature and search on the page for UXA you will find instructions.

---

### Post by mirobelix on 2016-02-16
Thanks for the links,
     the notebook seems to meet the requirements you listed.
     I created an Xorg.conf file at etc/X11 and pasted the description of     the Intel driver with UXA into it as you recommended, but     unfortunately, that didn't help.
     
     Since I get a proper resolution, if I start the notebook using GRUB     (holding left shift), I tried to create an Xorg.conf file by     stopping lightdm and then sudo X -configure, but unfortunately I get     error 2 stating "No devices to     configure. Configuration failed. (EE) Server terminated with error     (2). Closing log file.".
     
     I also tried to set the resolution explicitly with xrandr by     aquiring modeline information via cvt and then typing
     xrandr --newmode "1024x768_60new" 63.50 1024 1072 1176 1328 768 771     775 798 -hsync +vsync and
     xrandr --addmode LVDS1 "1024x768_60new"
     but with the second command I get
     X Error of failed request: BadMatch (invalid parameter attributes)
     Major opcode of failed request: 140 (randr)
     Minor opcode of failed request: 18 (RRAddOutputMode)
     Serial number of failed request: 27
     
     Note: After adding this new mode, starting into a proper resolution     via the GRUB menu seems not to work anymore.

---

