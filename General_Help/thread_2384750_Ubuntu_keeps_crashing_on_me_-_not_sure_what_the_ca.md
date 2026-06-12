---
title: "Ubuntu keeps crashing on me - not sure what the cause is"
date: 2018-02-11
forum: General Help
---

### Post by bzzzzz on 2018-02-11
Hi

I've not had problems with Ubuntu for years, but suddenly I seem to be experiencing glitches.  I'm running a fairly old laptop (HP 2230s) 

I know the battery is old, and I don't use it, except when it's plugged in.  

My recent problems have been the laptop automatically switches itself off for no apparent reason.

Also if the laptop is left on for around about 45 minutes it will more than likely crash - as in completely irresponsive.  The mouse pointer won't move and keys don't do anything.

Any guidance will be gratefully received

---

### Post by QIII on 2018-02-11
The very first thing that comes to mind with an older laptop displaying this sort of behavior is a thermal fault.

The first thing to check would be to see if the CPU cooler has fallen victim to a build up of dust kittens.   Get a can of compressed air and carefully blow it through the  cooling system from the exhaust side.  Use a toothpick or something similar to hold the fan in position because you may damage it if the flow of gas causes it to turn at a rate higher than its design allows.  Blowing air in from the intake side may just compact any foreign material even more.  Leave the computer off for a few hours because the cold gas from the can will have caused condensation that might be deposited on the internal components.

The next thing to check would be the state of the thermal compound between the HSF and the CPU (if you can get inside the machine easily, you can do both this and the suggestion above at once).  In all machines, thermal compound eventually dries and degrades to the point that it can become a hindrance to thermal transfer from the CPU to the HSF.  Clean the HSF and CPU, apply an appropriate amount of thermal compound and reinstall the HSF.

If that doesn't solve the issue, then we can look at other things.

---

### Post by gordintoronto on 2018-02-12
To see the actual temperatures, install lm-sensors. Then run: 
sudo sensors-detect

It will suggest adding a startup daemon, accept the suggestion and reboot. Then you can run the command:
sensors

You can probably find an online tutorial for opening up the laptop and cleaning it. First, BACKUP!

---

### Post by bzzzzz on 2018-02-12
Hi guys

Thanks for replying.  Hopefully we can get to the bottom of this

I tried giving a clean, but the shut downs just seem random rather than due to overheating.

I turned it on today and it shut down within 5 seconds
I turned it on again and it shut down before I could logon
I turned it on again and now it's been on for 5 -10 minutes

I ran the sensors command and this is what it gave me

@ubuntu:~$ sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:        +43.0°C  (crit = +256.0°C)
temp2:        +47.0°C  (crit = +92.0°C)
temp3:        +29.0°C  (crit = +105.0°C)
temp4:        +20.0°C  (crit = +92.0°C)
temp5:        +30.0°C  (crit = +110.0°C)

coretemp-isa-0000
Adapter: ISA adapter
Core 0:       +60.0°C  (high = +100.0°C, crit = +100.0°C)
Core 1:       +49.0°C  (high = +100.0°C, crit = +100.0°C)

---

### Post by QIII on 2018-02-12
OK.  Let's still work on temperatures.  It's not ruled out yet.  What you have there is a single reading at idle.  You might be spiking the temp periodically.

Open a terminal and issue

```
watch -n 1 sensors
```

This will give you a second-by-second reading from sensors.  Go about your normal business, but check your terminal often.  Let's see if temperatures get out of hand while you are running things.

If we rule that out, then we can look at other things.

---

### Post by bzzzzz on 2018-02-12
Okay i've got that now
what would be a dangerous temperature?

As I'm running a couple of programs

browser and spreadsheet and terminal I've seen it get up to high 40's

Is that high?

---

### Post by bzzzzz on 2018-02-12
It just crashed.

I can't see temperatures because it's frozen on the screen with the spreadsheet.  The computer has been on for around half an hour

---

### Post by gordintoronto on 2018-02-12
> **bzzzzz said:**
> 
I turned it on today and it shut down within 5 seconds
I turned it on again and it shut down before I could logon
I turned it on again and now it's been on for 5 -10 minutes
....


Then it's not overheating.

When my desktop randomly crashed, it turned out to be an ACPI issue, but it often ran for a few days before crashing.

I am no expert, but I think any temperature above 95C is "dangerous."

---

### Post by #&amp;thj^% on 2018-02-12
+1 ^^^^
Kind of a general range for most hardwre:**(high = +84.0°C, crit = +100.0°C)**
Some have even a higher Temp Threshold. 
But Heat is the worst enemy for all hardware.

---

### Post by bzzzzz on 2018-02-13
Is there a way for me to find what the temp was when it crashed?

---

### Post by QIII on 2018-02-13
You can keep a log that you can look at when you restart.

Create a new text file in your /home and call it temp.log

You can log the temperature every three seconds by issuing this in the terminal:

```
watch -n 3 "sensors | grep Core >> /home/you/temp.log"
```

Leave that running and go about your business.  Have a look at that after a crash and see if you get a spike.

---

### Post by dragonfly41 on 2018-02-14
Another tool to install is gkrellm and set alerts.

Here is a useful guide .. [https://warrenpost.wordpress.com/2010/05/27/gkrellm/](https://warrenpost.wordpress.com/2010/05/27/gkrellm/)

GKrellM is found in Synaptic.  Plus a bunch of plugins.

---

