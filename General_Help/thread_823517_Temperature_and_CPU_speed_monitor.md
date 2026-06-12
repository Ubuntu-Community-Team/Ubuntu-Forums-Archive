---
title: "Temperature and CPU speed monitor????"
date: 2008-06-09
forum: General Help
---

### Post by jrharvey on 2008-06-09
Ok so I recently Overclocked my Core2 Quad 2.4ghz to 3.0ghz. I did all my test in windows to get it stable and right now it works flawlessly while running in windows, even at full load for hours. In ubuntu, it obviously still states that the speed is 2.4 because the processor is  rated at that but I want a program that will tell me the TRUE processor speed (not the rated). I also want to be able to monitor my temperature, just to make sure that ubuntu is adjusting the fan properly. Anything would help.

---

### Post by jrharvey on 2008-06-09
I may not be getting any replies because I know alot of people here look down on overclocking but i will tell you that I need every bit of juice i can get for work.

---

### Post by 1337 on 2008-06-09
I would recommend you Conky or GkRellm as addition for LMSensors package which read all your hardware sensors information. They are in Ubuntu repos.

Regards

---

### Post by jrharvey on 2008-06-09
Ok, I installed all of those already from the repos but could not figure out how to run the commands. None of those have a GUI and I do not know the terminal commands for those programs.

---

### Post by 1337 on 2008-06-09
Use search function of this forum, there are plenty of howtos on this forum how to install lmsensors with Xsensors/Conky/GKrellm.

You can try this one also: [https://help.ubuntu.com/community/SensorInstallHowto](https://help.ubuntu.com/community/SensorInstallHowto)

Regards

---

### Post by bingoUV on 2008-06-09
For a start, you can add the following applet to your gnome-panel. It is  pre-installed.

1. CPU frequency scaling monitor : Add it 4 times. In Preferences, set them to monitor core 1, 2, 3 and 4 respectively.

---

### Post by jrharvey on 2008-06-09
> **bingoUV said:**
> For a start, you can add the following applet to your gnome-panel. It is  pre-installed.

1. CPU frequency scaling monitor : Add it 4 times. In Preferences, set them to monitor core 1, 2, 3 and 4 respectively.

The applet does not display a temperature. I forgot to mention that.

---

### Post by jrharvey on 2008-06-09
2 THINGS

#1 the temperature does not read at all. (as seen in the pic)

#2 My CPU "should" be overclocked at 3.0 (as seen in CPU-Z) but Conky does not show this. One of the 2 are wrong.

---

### Post by jrharvey on 2008-06-10
Ok i have tried everything i can in synaptic. All CPU temp monitors do not work for me.

---

### Post by bluepowder7 on 2008-06-10
i used the lmsensors thing, and computertemp (from berlios) for the actual display.  there's a decent how-to somewhere...  lemme see...

[http://www.xawk.com/ubuntu-cpu-temperature.html](http://www.xawk.com/ubuntu-cpu-temperature.html)

read it and do it.  i installed xsensors but didn't like it, so i got the other one:

[http://computertemp.berlios.de/index.php](http://computertemp.berlios.de/index.php)

---

### Post by jrharvey on 2008-06-11
> **bluepowder7 said:**
> i used the lmsensors thing, and computertemp (from berlios) for the actual display.  there's a decent how-to somewhere...  lemme see...

[http://www.xawk.com/ubuntu-cpu-temperature.html](http://www.xawk.com/ubuntu-cpu-temperature.html)

read it and do it.  i installed xsensors but didn't like it, so i got the other one:

[http://computertemp.berlios.de/index.php](http://computertemp.berlios.de/index.php)

Wow, thank you. This is the first real reply that might solve this problem because i did not know you had to configure lm-sensors which may be why my CPU temp is not working. IDK but i will try this and get back.

---

### Post by forestpixie on 2008-06-11
If you try xsensors and you find an error when running it, as I did, edit the launcher to 

/usr/bin/xsensors -c /etc/sensors3.conf

---

