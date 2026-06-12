---
title: "check system temp"
date: 2007-06-04
forum: General Help
---

### Post by rob1101 on 2007-06-04
what can i do to monitor my system temp? such as the processor temp, HDD temp, ect...

---

### Post by soze on 2007-06-04
> **rob1101 said:**
> what can i do to monitor my system temp? such as the processor temp, HDD temp, ect...

Rightclick on your taskbar, select "add to panel" then select "hardware sensors monitor"

---

### Post by rob1101 on 2007-06-04
> **soze said:**
> Rightclick on your taskbar, select "add to panel" then select "hardware sensors monitor"

i don't seem to have "hardware sensors monitor" the closest thing i have to that is a system monitor but that just shows the resources.

---

### Post by glósóli on 2007-12-07
> **rob1101 said:**
> i don't seem to have "hardware sensors monitor" the closest thing i have to that is a system monitor but that just shows the resources.

yeah, it's the same for me [ubuntu 7.10]
why that?

plesae help, thank you!

---

### Post by bingoUV on 2007-12-07
Install lm_sensors. Run sensors-detect as root.

---

### Post by glósóli on 2007-12-07
thanks!

but isn't it lm-sensors another util?

I was just wondering why eveybody else has this hw sensors monitor, but my ubuntu don't.. :(

---

### Post by dave37 on 2007-12-07
As BingoUV noted, install **and** configure lm-sensors (do a search on these boards, there's a very good howto) and then you need to install a gnome (I'm assuming you're running gnome) applet.  

I've used sensors-applet (you can install using apt or aptitude at the command line) but am currently using computer temperature monitor, available here [http://computertemp.berlios.de/](http://computertemp.berlios.de/)  which I like better, there are packages listed on that link page.

---

### Post by glósóli on 2007-12-07
ok, I succeded installing sensors-applet-1.8.2!

just found one sensors, should be at least one more..

anyway, now I'll have a try on lm-sensors!!

[OT: after unpacking the tar.gz in a random folder, and compiling everything, can I delete the folder obtained out of the tar.gz, right??  ]

---

### Post by bingoUV on 2007-12-08
> **glósóli said:**
> ok, I succeded installing sensors-applet-1.8.2!

just found one sensors, should be at least one more..

anyway, now I'll have a try on lm-sensors!!

[OT: after unpacking the tar.gz in a random folder, and compiling everything, can I delete the folder obtained out of the tar.gz, right??  ]


Isn't it available from repositories? Try synaptic

---

### Post by glósóli on 2007-12-09
> **bingoUV said:**
> Isn't it available from repositories? Try synaptic

why that? I already installed it...i was just curious about the package you download to install generic programs/drives...once installed they can be safely removed, but I'd like a confirm just to be sure not to make a mess! ;) [litlle OT btw, I know..]

---

### Post by dave37 on 2007-12-09
You still need to configure lm-sensors.  Sensors-applet is merely a front end for lm-sensors.  Follow the instructions detailed here and you should have no problems.

[http://ubuntuforums.org/showthread.php?t=2780&highlight=sensors](http://ubuntuforums.org/showthread.php?t=2780&highlight=sensors)

---

### Post by drs305 on 2007-12-09
> [OT: after unpacking the tar.gz in a random folder, and compiling everything, can I delete the folder obtained out of the tar.gz, right?? ]

Yes

---

### Post by bingoUV on 2007-12-09
Yes, but it is orders of magnitude more convenient to update, remove, configure and monitor your installed software with package management. You would not even need to know whether you can delete the folder after installing :). Though it is good to know in general.

---

