---
title: "[SOLVED] Constant crushes"
date: 2008-05-31
forum: General Help
---

### Post by Sordelka on 2008-05-31
Hello,

I am experiencing constant system shutdowns. It happens randomly and before shutdown, the system issues the error beep signal. 

What can I do to find out why it happens?

---

### Post by pytheas22 on 2008-05-31
Look at the system log.  You can access it either by navigating to the /var/log directory or using the GUI found under System>Administration>System Log.  Look for entries that match the time the system crashes, and hopefully it will tell you what's wrong.

Also, is the system just turning off or is it going through a clean shutdown process (i.e. do you see the Ubuntu logo and the orange bar as it shuts down)?

---

### Post by Sordelka on 2008-05-31
I see the shutdown logo and everything as if I shut it down, but I did not and I did not put any shutdown timers on!

---

### Post by pytheas22 on 2008-05-31
> I see the shutdown logo and everything as if I shut it down, but I did not and I did not put any shutdown timers on!

That tells us at least that the system is remaining stable when it goes down, so it's unlikely that something is crashing.  Please take a look at the logs and try to figure it out.  If you can't see anything that looks relevant to your problem, attach your syslog file here and someone can take a look.

---

### Post by Sordelka on 2008-06-01
Next time it does that, I certainly will.

---

### Post by Sordelka on 2008-06-02
Found out that when system shuts down it says that acpi critical temperature reached. It happens only playing a game (any game). How could it be that it reaches 135 degrees celcius...

---

### Post by leito666 on 2008-06-02
I was just going to tell you that, check if all PC fans are working correctly.

---

### Post by Sordelka on 2008-06-02
f71882fg-isa-0a10
Adapter: ISA adapter
3.3V:        +3.46 V
Vcore:       +1.14 V  (max =  +2.04 V)   
Vdimm:       +1.87 V
Vchip:       +1.97 V
+5V:         +5.21 V
12V:        +14.27 V
5VSB:        +6.85 V
3VSB:        +3.44 V
Battery:     +3.33 V
CPU:        1930 RPM
System:     1421 RPM
Power:      1483 RPM
Aux:           0 RPM  ALARM
CPU:         +53.0°C  (high = +85.0°C, hyst = +81.0°C)  
                      (crit = +100.0°C, hyst = +96.0°C)  sensor = transistor
System:      +33.0°C  (high = +85.0°C, hyst = +81.0°C)  
                      (crit = +100.0°C, hyst = +96.0°C)  sensor = transistor

coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +65.0°C  (crit = +85.0°C)                  

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +64.0°C  (crit = +85.0°C)

---

### Post by Sordelka on 2008-06-02
THe reason is summer lol. My fan speeds are not high enough and both cores overheat when using some graphical game... :-( No games for summer

---

