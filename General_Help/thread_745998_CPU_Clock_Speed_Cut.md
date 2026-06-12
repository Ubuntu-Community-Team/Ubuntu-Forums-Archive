---
title: "CPU Clock Speed Cut"
date: 2008-04-05
forum: General Help
---

### Post by The AlGorenator on 2008-04-05
I have a 2.00 GHz Intel Pentium M processor.

For some odd reason, it will only run at 800mhz under ubuntu.

I'm thinking this is due to some vicious power management, as it's a laptop.

Anyone care to help me put it back up to what it runs at under windows?

---

### Post by NightwishFan on 2008-04-05
Perhaps disabling the powernowd service? It may just be throttled, both of my cores sit comfortably at 1ghz until they are needed. Disabling may be rash. Try running a demanding application and see if it scales back up to normal.

---

### Post by The AlGorenator on 2008-04-05
I've done some searching around. Apparently, this is a documented bug with cpufreq.

It is only allowing the CPU to operate at this low speed. I attempted to remove CPU freq, however, upon re-booting, i found that my task bar was no longer present.

Using ctrl + alt + t, i was able to open a console to re-install cpufreq, and then restarted x.

upong logging in again, i had my taskbar.

I assume this means that cpufreq is causing my problem and unremovable.

halpz?

---

### Post by The AlGorenator on 2008-04-05
> **The AlGorenator said:**
> 
I assume this means that cpufreq is causing my problem and unremovable.


Okay, strike that.

I've managed to remove cpu freq and keep teh task bar [trying to keep teh cpu frequency applet in it while removing cpufreq was the problem]

regardless of this, still only 800/2000 even under heavy load.

---

### Post by The AlGorenator on 2008-04-06
Okay, i've tried a number of different CPU scaling apps, and still my CPU refuses to move up to the full 2ghz it is capable of.

I know it can as it used to. My running theory is that a a problem with the kernel is to blame.

Should i attempt to upgrade or downgrade?

If neither, then what?

---

### Post by notna01 on 2008-04-06
if you want to check your speed on windows, get cpu-z (google it)

Maybe its running so low because you are on battery when you press the on button?

---

### Post by The AlGorenator on 2008-04-06
> **notna01 said:**
> if you want to check your speed on windows, get cpu-z (google it)

Maybe its running so low because you are on battery when you press the on button?

Windows also reported my CPU to be running at ~800mhz.

It must be noted, however, running the command 

```
cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_frequencies
```

produces the output 

```
2000000 1600000 1333000 1067000 800000 
```

showing that my CPU is capable of doing 2ghz.

I must also note that the laptop the CPU is in has a problem with the battery charger, and for some reason the battery will not charge [not the battery itself, the actual charging mechanism] and due to this, the system is CONSTANTLY on ac power.

---

### Post by notna01 on 2008-04-06
> **The AlGorenator said:**
> 
I must also note that the laptop the CPU is in has a problem with the battery charger, and for some reason the battery will not charge [not the battery itself, the actual charging mechanism] and due to this, the system is CONSTANTLY on ac power.

that is probably your problem. Try going into the BIOS and setting your CPU settings.

---

### Post by The AlGorenator on 2008-04-06
> **notna01 said:**
> that is probably your problem. Try going into the BIOS and setting your CPU settings.

I think i agree with this, as my BIOS says that system performance is being limited as it 'cannot recognise the type of power adapter you are using', even though i am using the one that came with it.

Can i change my BIOS to another version all together to circumvent this?

---

