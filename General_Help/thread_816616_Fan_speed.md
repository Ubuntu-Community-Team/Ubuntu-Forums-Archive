---
title: "Fan speed"
date: 2008-06-02
forum: General Help
---

### Post by dbn79 on 2008-06-02
Hello,

I am not sure if this falls into general help or somewhere else, but outside of an older thread that I've followed, I'll try here.

I am new to Ubuntu and have been having issues with my Sony PCV-RX550. When running xsensors my fan1 is running at ~4200 RPM - so it is a little loud. I've been working through directions found online ([http://ubuntuforums.org/showthread.php?t=2780](http://ubuntuforums.org/showthread.php?t=2780) and other links) and seem to be making some progress, but I can't get the fan to slow down (expect when running pwmconfig correlation) - I'm trying to use ls sensors.

I've been able to change some of my settings as follows (not sure how useful they are, but at least I've been able to change them):

Settings of hwmon0/device/pwm2:
Depends on
Controls hwmon0/device/fan2_input
MINTEMP=37
MAXTEMP=41
MINSTART=90
MINSTOP=75
MINPWM=75
MAXPWM=80

Settings of hwmon0/device/pwm1:
Depends on hwmon0/device/temp1_input
Controls hwmon0/device/fan1_input
MINTEMP=37
MAXTEMP=41
MINSTART=150
MINSTOP=135
MINPWM=135
MAXPWM=140

When I run 'fancontrol start' I get the following message:
Enabling PWM on fans...
Starting automatic fan control...
/usr/sbin/fancontrol: line 265: ${tsens}: ambiguous redirect
Error reading temperature from /sys/class/hwmon/
Aborting, restoring fans...
Verify fans have returned to full speed

So close (I think), but not there yet.

Not sure if this is useful, but when running "sensors" I get:
w83627hf-isa-0290
Adapter: ISA adapter
VCore 1: +1.71 V (min = +1.65 V, max = +2.05 V)
VCore 2: +0.05 V (min = +1.65 V, max = +2.05 V)
+3.3V: +3.33 V (min = +2.82 V, max = +3.79 V)
+5V: +5.13 V (min = +2.61 V, max = +3.09 V)
+12V: +11.80 V (min = +14.47 V, max = +11.61 V)
-12V: -12.11 V (min = +1.95 V, max = -1.83 V)
-5V: +3.54 V (min = +5.10 V, max = +0.93 V)
V5SB: +5.56 V (min = +5.91 V, max = +5.03 V)
VBat: +1.55 V (min = +1.76 V, max = +0.29 V)
fan1: 4218 RPM (min = 3534 RPM, div = 2)
fan2: 2177 RPM (min = 1584 RPM, div = 4)
fan3: 0 RPM (min = 3082 RPM, div = 2)
temp1: -48.0°C (high = +123.0°C, hyst = -18.0°C) sensor = thermistor
temp2: +38.0°C (high = +80.0°C, hyst = +75.0°C) sensor = diode
temp3: +37.0°C (high = +80.0°C, hyst = +75.0°C) sensor = thermistor
cpu0_vid: +1.750 V
beep_enable:enabled

Any suggestions? Thanks for any help...I'd like to actually run Ubuntu and move away from Windows a bit, but this fan speed is too much!

---

### Post by unutbu on 2008-06-02
Take a look at [http://ubuntuforums.org/archive/index.php/t-250025.html](http://ubuntuforums.org/archive/index.php/t-250025.html).

I am guessing your start script might have a malformed or missing FCTEMPS line.

---

### Post by dbn79 on 2008-06-03
Still seem to be stuck.

Any suggestions on how to check that? Besides running pwmconfig and then seeing configuration through the prompts included in that program, which gets me the output at the start of my initial post that has no mention of FCTEMPS, I don't seem to have access or maybe the right commands to edit - "fancontrol".  Am I looking in the right place? Any reason I don't have FCTEMPS or FCFANS? Is that significant?

---

### Post by unutbu on 2008-06-03
When you run fancontrol, do you type

```
% fancontrol start
```

? If so, it appears just from looking at the script /usr/sbin/fancontrol, that "start" must be the name of a file. So I think you would want to edit "start" to include some line which says something like

```

FCTEMPS=1-0290/pwm2=1-0290/temp2_input

```

To edit the file "start" you could use gedit: click Applications>Accessories>Text Editor or type

```
gedit start
```

---

### Post by dbn79 on 2008-06-03
Thanks for getting back to me.

I do type "fancontrol start" to get things running, although I understand I can also type "fancontrol stop" after the "start" command (?) starts working to stop the program (I think).

When I type "gedit /etc/fancontrol" or "gedit start" I get "cannot open display"; I am in root.

---

### Post by dbn79 on 2008-06-03
I think I got it working!

---

### Post by dbn79 on 2008-06-03
Well minus the fact that when starting it it doesn't seem to want to allow me to go back to the prompt...or if I start a new terminal screen, "fancontrol stop" doesn't seem to stop it.  More work to do...

---

### Post by unutbu on 2008-06-03
This page [http://ubuntuforums.org/showthread.php?t=42737](http://ubuntuforums.org/showthread.php?t=42737)
gives instructions whereby you can type

```
sudo /etc/init.d/fancontrol start
sudo /etc/init.d/fancontrol stop
```

Maybe that will help.

What page are you looking at that tells you to type 

```
fancontrol start
```
?

---

