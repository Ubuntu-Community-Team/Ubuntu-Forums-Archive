---
title: "[Solved] Real time motherboard sensor monitoring"
date: 2013-03-24
forum: General Help
---

### Post by ozark_hillbilly on 2013-03-24
Is there any program available to use on the Unity platform (12.4 LTS) to display cpu/motherboard sensor data in an active/realtime format? I know about lm-sensors that is run in terminal mode. Has anyone setup and ran Alex Murray's Hardware Sensor Indicator program on Unity?  link:  Launchpad.net/indicator-sensors

Ed

---

### Post by ManamiVixen on 2013-03-24
Install psensor

sudo apt-get install psensor

That lists all detected sensors in a drop-down menu on the panel.

---

### Post by gifford on 2013-03-24
I use GKrellm to monitor cpu temp, cpu usage and other info in realtime. Lm-sensors supplies the data. I think conky will do the same.

---

### Post by ozark_hillbilly on 2013-03-25
How do you link lm-sensors to GKrellm? I have both already installed and have good data from lm-sensors using terminal mode.

For installation of the weather plug-in referencing this file:

GKrellWeather:  GKrellM Weather Plugin
Author:         Franky Lam <franky@frankylam.com>
Homepage:       [http://www.frankylam.com/](http://www.frankylam.com/)

install:

    make
    make install (as root)

require:
    - wget or LWP

gkrellweather is copyright (c) 2001 by Franky Lam.

What else is required besides make & make install? It seems in terminal mode additional parameters would be necessary. ???

Still coming up to speed on GKrellm,


Ed

---

### Post by gifford on 2013-03-25
I use Synaptic Package Manager to install, it includes various add-ons for GKrellM. I'm attaching a screenshot for you to view.
[ATTACH=CONFIG]240543[/ATTACH]

---

### Post by ozark_hillbilly on 2013-03-25
Gifford,

That GKrellm setup looking at your screenshot is way cool.....I'm persistent so I hope to get there as well....  Ed

---

### Post by NetworkNerd7 on 2013-03-25
I am curious about this too, is there a Linux version of speedfan available?

---

### Post by ozark_hillbilly on 2013-03-25
making progress....trying to configure sensors under Built-Ins.... ????

ed

---

### Post by gifford on 2013-03-25
Not sure what is causing the problem, but you could remove gkrellmapcupsd. I think that temps & voltages is built in to GkrellM. Right click on the desktop gkrellm and go to configuration. Under builtins is a listing for sensors, cpu, etc.

---

### Post by ozark_hillbilly on 2013-03-25
Gifford,

It was the right-click holding me up!
AND I was not clicking on the little tiny arrow at the beginning of each line!!!!

Got it!  GKrellm SERIOUSLY ROCKS!!!!!!!

Still need to figure how how to assign correct weather station for weather data. ?????

Ed

---

### Post by gifford on 2013-03-25
I have never used the weather station. Instead, I use my-weather-indicator with wunderground.com as the data provider. Works Great!
Glad you like GKrellM, I've used it for years.

---

### Post by gifford on 2013-03-26
If by speedfan you mean to monitor and control fan speeds, that is a part of GKrellM.

---

