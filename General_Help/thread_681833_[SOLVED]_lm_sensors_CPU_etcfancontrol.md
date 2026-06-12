---
title: "[SOLVED] lm sensors CPU /etc/fancontrol"
date: 2008-01-29
forum: General Help
---

### Post by santaslittlehelper on 2008-01-29
Hi 

I got a problem with configuring /etc/fancontrol I will try to explain best I can, here is what happens.

I have set the CPU fan to start just below 1700 RPM (which is the RPM for quiet or not so quiet, which is why I would like to start at that RPM) with the fancontrol config and this will do quit well for a long time, the problem comes later. When the computer have been up for a long time doing various CPU intense tasks the fancontrol config kind of skips out on me. 

The CPU fan will start to switch very fast between say 1600 RPM and 2300 RPM, (this happens even when idle after x hours uptime, if CPU intense tasks has been done) really just doing it's job adjusting the temperature. 

But the temperature falls very quickly so the fan will adjust, then the temperature raises very quickly again and so do the fan (again even when idle) so what I am left with at this time is a fan that continuously spins up and down way to quickly generating a very annoying sound. 

I have tried various configurations but after x hours, if doing CPU intensive task once in a while, the outcome will be that the fan is going in to this contentiously circle of spinning up and down.

Do anyone have suggestions to how I might need to configure /etc/fancontrol?
Also if anyone have suggestion to a Fan Control System that might be worth buying I would like to know about it, but please be specific.

M2N32-SLI/DELUXE 
AMD 64 X2 5200
Zelman 9700LED

Hope I am making sense here.

edid
I think I got the right config now, maybe a bit early to say.
My guess it that I let the fan drop to low, now I have set it so it will not drop below 1550 RPM at any time. 

Settings of hwmon1/device/pwm1:
  Depends on hwmon1/device/temp1_input
  Controls hwmon1/device/fan1_input
  MINTEMP=26
  MAXTEMP=46
  MINSTART=125
  MINSTOP=120
  MINPWM=115
  MAXPWM=225

Maybe sometime you should not think to hard about and just follow the defaults. :)

MINTEMP=24
MAXTEMP=48
MINSTART=150
MINSTOP=100
MINPWM=90
MAXPWM=255

Lets see :)

---

