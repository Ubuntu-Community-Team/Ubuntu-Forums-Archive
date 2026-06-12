---
title: "System crash, mouse and keyboard freezes"
date: 2020-07-31
forum: General Help
---

### Post by MgFrobozz on 2020-07-31
[COLOR=#000000][INDENT]I'm getting a crash multiple times a day with these symptoms:

Mouse freezes and mouses led goes dark
No keyboard response
Can't ssh into system
System doesn't return pings

I'm running:[/INDENT]
[INDENT]Ubuntu 18.04.4 LTS
Linux 4.15.0-112-generic #113-Ubuntu SMP Thu Jul 9 23:41:39 UTC 2020 x86_64 x86_64 x86_64 GNU/Linux
Asus B450M motherboard
Ryzen 2600 CPU

It has the feel of a thermal lock-up, but the sensors are showing cpu temperature around 45-50 degrees C. It's warm-ish here (about 85 F outside and mid-70s inside). I'm surprised that the cpu temp is that low. Sensors also show a single fan, with **fan speed 0 rpm**. I've checked that both the cpu fan and the chassis fan are running, and that the chassis fan is plugged into the 'CHA FAN' connection, and that the cpu fan is plugged into the 'CPU FAN' connection. The connectors are keyed, and the plug is on the right way on both. Both fans are running more slowly than I would expect. I'm wondering whether the thermal control loop is broken in some way.[/INDENT]
[/COLOR][COLOR=#000000][INDENT]
I can see both k10temp and lm78 kernel modules installed, and /etc/sensors3.conf looks reasonable, on first inspection. There are no files other than .placeholder in /etc/sensors.d. I'm wondering whether I need to customize the sensors in order to get the thermal control working, but I can't find details on how to do that for the b450m/ryzen2600 combination.

Any suggestions would be gratefully received ...[/INDENT]
[/COLOR]

---

### Post by CatKiller on 2020-07-31
That doesn't really say thermal to me. Going increasingly slowly as it throttles followed by a shutdown are the symptoms that you'd expect to see if it were overheating.

Not being able to read the sensor chip on the motherboard is relatively standard. There are probably ways you could do so if you wanted to, but it's not really a big deal for now. You can probably adjust the fan curve in the UEFI if you want more or less cooling; the UEFI *can* read the sensor chip and will adjust your fans accordingly.

Iffy memory access (RAM timings, badly behaved driver, that kind of thing) or wobbly voltages (spike/droop in load, weak power supply, overclocking, and so on) would be my first thoughts of where to start looking. 

Intermittent faults, particularly intermittent freezes, are an absolute pain to troubleshoot. 

It's probably worth seeing if there's a UEFI update you can use. There have been a few specifically for memory stability on the Ryzen platform. Plus checking that your UEFI settings are good so that you aren't inadvertently overclocking or otherwise putting your system outside of what it can handle.

---

### Post by HermanAB on 2020-08-01
"Mouse LED goes dark" - I think I'm about 99.875% sure that you have a bad PSU.

---

### Post by dinkidonk on 2020-08-01
Have you tried to look in the syslog to see what happens when the system freezes? File: /var/log/syslog

The Ryzen 2*** series has caused all sorts of trouble with random lockups and what not. Some where fixed with BIOS updates and/or settings in BIOS, others where fixed with firmware updates. If your BIOS is not up to date, you could try to update it - but check the syslog for starters, entries in the log may help solve your problem :)

---

### Post by Autodave on 2020-08-01
I missed that part, Herman!  Yes: surely sounds like a bad PSU.  One other possibility: how may things to you have plugged into USB ports?  You could have something there pulling the 5 volt line low.

---

### Post by MgFrobozz on 2020-08-01
dinkidonk, no information in the log around that time (except for log-and-drop from iptables).

---

### Post by MgFrobozz on 2020-08-01
Autodave, my USB usage is:
Microsoft basic optical mouse V2.0
Coolermaster CM Storm keyboard

---

### Post by MgFrobozz on 2020-08-01
[duplicate post]

---

### Post by MgFrobozz on 2020-08-01
Still checking for thermal issues. I ran 'sensors-detect --auto', which reported:
[COLOR=#000000]Trying family `ITE'...                                      Yes
Found unknown chip with ID 0x8655
    (logical device 4 has address 0x290, could be sensors)
[/COLOR]
Web commentary suggested that this family  is covered by it87.ko, The current it87.c doesn't include support for IT8655.  

The IT8665 is probably an environmental control chip like the IT8720, which has a thermal input and a fan connection. Missing support would explain:
* the 0 RPM fan speed
* the CPU temp that seems oddly low on a hot day
* the apparently low (but not 0) cpu fan speed 

Other Asus B450M users at [https://github.com/lm-sensors/lm-sensors/issues/195](https://github.com/lm-sensors/lm-sensors/issues/195) may be encountering the same issue. Someone there said that using [https://github.com/a1wong/it87](https://github.com/a1wong/it87) (a fork) worked for t[FONT=arial]hem, but that repo has been pulled with the explanation "[COLOR=#24292E]I have been unable to meet support demands for this driver". 

I cloned that driver, reverted the removal, and I'm investigating what it will take to fork the master it87 and add only 8665 support, with the goal of getting support into the master branch. It looks like the LT8655 is close to the LT8628 (a supported chip), except that it supports only 3 fans (vs 6 for the LT8628).[/COLOR][/FONT]

---

### Post by MgFrobozz on 2020-08-03
A little more information ... today, about 5 minutes after boot on a much cooler morning, the same freeze except that the mouse cursor could still be used (but mouse click did nothing). GIven the ambient temperature and short time the system was running, it probably was not a thermal lockup. The 0 rpm fanspeed is apparently a red herring.

There was a message in the log 2 seconds before the lockup about bluetooth service ...

*Aug  2 17:47:03 localhost pulseaudio[2227]: [pulseaudio] bluez5-util.c: GetManagedObjects() failed: org.freedesktop.DBus.Error.TimedOut: Failed to activate service 'org.bluez': timed out (service_start_timeout=25000ms)*

This doesn't seem a likely cause for the lockup, but I disabled bluetooth service anyway (I don't need it). At the time of the lockup, there was a blast of NULLs written to the log, but no fault messages, and I have no idea how to tell where the nulls came from.

---

### Post by dinkidonk on 2020-08-04
> **MgFrobozz said:**
> At the time of the lockup, there was a blast of NULLs written to the log

If you by this means that there was a lot of bytes with a value of 0x00 written to the log, this is usually caused by a hard reset which causes the log-file not to be closed properly. The null's are reserved space prior to a file write / file flush from memory which is interrupted. When the system boots after a hard reset the syslog may have entries which states something about a dirty volume which has to be (and is) cleaned before continuing because of the hard reset.

If your problem is a resent issue started for no apparent reason, then I would guess that it is hardware related. The most obvious culprits are a faulty system drive causing corruption in the system / initramfs (check S.M.A.R.T. data for the drive for bad or pending sectors) or faulty memory modules (check with memtest). If none of those gives any clues, the next thing to check is the GPU and the PSU.

---

