---
title: "Ubuntu server crash"
date: 2013-01-22
forum: General Help
---

### Post by prem1er on 2013-01-22
I'm having issue with a headless server running Ubuntu 10.04 (with lightweight gnome gui). I just recently built the server. The last couple of days the server has been having some issues. It will freeze up to the point where there is no longer a network connection, I can plug in a usb mouse and keyboard with a monitor and it won't display anything, because the mouse and keyboard don't wake it from sleeping the display. The only option I have is to reboot the machine with the power button and boot it back up. I can then log in and begin to check error messages that may have occurred. I don't see anything in the logs that looks to be wrong. Can anyone point me in the direction of which log I should be looking in and also if this log persists after the machine is rebooted? I need a starting point to help solve this one. TIA.

---

### Post by tgalati4 on 2013-01-22
First run memtest for several cycles.  Some versions have a bug in test #7 that causes errors at 129 MB--just ignore those errors.  If your RAM passes, then check the voltages of your power supply either through BIOS or with a voltmeter plugged into a spare power connector.  Reseat the cards and ribbon cables in the machine.  Put a monitor on it and keep a terminal open at all times so you can see any syslog messages or kernel panics.  Also put ssh on the machine and log in from another machine so that if it does freeze up, you might be able to read the logs from another machine.

---

### Post by prem1er on 2013-01-23
I ran the memtest and reseated the ram and pins. Everything was OK. You suggested leaving myself ssh'd into the machine, but what log should I be tailing while I'm ssh'd? Thanks for the suggestions.

---

### Post by Crafty Kisses on 2013-01-23
Could be memory allocation, just a thought

---

### Post by prem1er on 2013-01-23
> **Crafty Kisses said:**
> Could be memory allocation, just a thought

How could I rule this out?

---

### Post by prem1er on 2013-01-23
Just a thought. I installed Ubuntu 10.04 on some very new hardware. Could something in the kernel or drivers be having issues with the newer hardware?

---

### Post by tgalati4 on 2013-01-23
That's possible, but usually an older kernel just won't recognize something important like a SATA controller.  Then you won't have access to any disks.  And you would be here with a different question.  

If you page through dmesg, you will get a pretty extensive rundown as to how the kernel detects and handles your hardware.  If your machine boots, then that's 90% success.

I like to dmesg | tail -f but that doesn't work with the lastest distros.  So you can use it on 10.04 or tail syslog or kernel.log or just about anything in /var/log.

Because you haven't gotten any error messages so far, I suspect a hardware problem.  Did you verify your voltages while running?

I rebuild a client's machine yesterday that lost USB ports.  A system fan had frozen completely and somehow drew enough power to shut down the USB subsystem.  Strange but true.  Removed the fan (who needs a fan?) and he was up and running.

---

### Post by prem1er on 2013-01-23
> **tgalati4 said:**
> That's possible, but usually an older kernel just won't recognize something important like a SATA controller.  Then you won't have access to any disks.  And you would be here with a different question.  

If you page through dmesg, you will get a pretty extensive rundown as to how the kernel detects and handles your hardware.  If your machine boots, then that's 90% success.

I like to dmesg | tail -f but that doesn't work with the lastest distros.  So you can use it on 10.04 or tail syslog or kernel.log or just about anything in /var/log.

Because use haven't gotten any error messages so far, I suspect a hardware problem.  Did you verify your voltages while running?

I rebuild a client's machine yesterday that lost USB ports.  A system fan had frozen completely and somehow drew enough power to shut down the USB subsystem.  Strange but true.  Removed the fan (who needs a fan?) and he was up and running.

Here's my sensor output
```
:~/.config$ sensors
atk0110-acpi-0
Adapter: ACPI interface
Vcore Voltage:     +0.94 V  (min =  +0.80 V, max =  +1.60 V)
+3.3V Voltage:     +3.29 V  (min =  +2.97 V, max =  +3.63 V)
+5V Voltage:       +5.06 V  (min =  +4.50 V, max =  +5.50 V)
+12V Voltage:     +12.33 V  (min = +10.20 V, max = +13.80 V)
CPU Fan Speed:    1403 RPM  (min =  600 RPM)
Chassis Fan Speed:   0 RPM  (min =  600 RPM)
Power Fan Speed:     0 RPM  (min =  600 RPM)
CPU Temperature:   +26.0°C  (high = +60.0°C, crit = +95.0°C)  
MB Temperature:    +38.0°C  (high = +45.0°C, crit = +75.0°C) 
```

And with my 2 case fans

```

atk0110-acpi-0
Adapter: ACPI interface
Vcore Voltage:     +0.94 V  (min =  +0.80 V, max =  +1.60 V)
+3.3V Voltage:     +3.31 V  (min =  +2.97 V, max =  +3.63 V)
+5V Voltage:       +5.06 V  (min =  +4.50 V, max =  +5.50 V)
+12V Voltage:     +12.28 V  (min = +10.20 V, max = +13.80 V)
CPU Fan Speed:    1427 RPM  (min =  600 RPM)
Chassis Fan Speed:1119 RPM  (min =  600 RPM)
Power Fan Speed:   837 RPM  (min =  600 RPM)
CPU Temperature:   +27.0°C  (high = +60.0°C, crit = +95.0°C)  
MB Temperature:    +38.0°C  (high = +45.0°C, crit = +75.0°C) 

```

---

### Post by tgalati4 on 2013-01-23
VCore seems low, you might want to look up what a Core2 Duo requires.  Undervolting can cause lockups.  Are you overclocking at all?  Try declocking and see if that improves stability.

---

