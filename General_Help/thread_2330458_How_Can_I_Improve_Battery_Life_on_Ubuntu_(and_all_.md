---
title: "How Can I Improve Battery Life on Ubuntu (and all other Linux distros)?"
date: 2016-07-11
forum: General Help
---

### Post by jonathan90 on 2016-07-11
I'm running Ubuntu Trusty on my laptop and it's really eating away at my battery. Although my laptop is a couple years old, the battery still lasted about 2 hours on Windows 7, but it only lasts about half an hour on Linux. After using Ubuntu for almost a year, the battery life can only last 30 minutes on Windows as well. I heard the problem was due to Nvidia's graphics drivers being very resource intensive, but I'm not sure. I might be getting a new laptop or new laptop battery soon, so what can I do to increase the battery life so it doesn't wear away so quickly when running Linux? Thanks!

---

### Post by HermanAB on 2016-07-11
Switch to a DE that is not so graphics intensive, such as XFCE or LXDE.  The machine will be more responsive and your battery will last longer.

---

### Post by mastablasta on 2016-07-12
specs? currently used drivers?

there are tlp and various other power management programs. but you need ot see first what is drawing the power.

on linux i too have about 20-30% worse battery time.

---

### Post by Linuxisfast on 2016-07-12
If its discrete nvidia, install drivers, definitely install TLP, on my old x220 I get same batt life as with Windows 7.

---

### Post by Roland_Msl on 2016-07-12
> **jonathan90 said:**
> I'm running Ubuntu Trusty on my laptop and it's really eating away at my battery. Although my laptop is a couple years old, the battery still lasted about 2 hours on Windows 7, but it only lasts about half an hour on Linux. After using Ubuntu for almost a year, the battery life can only last 30 minutes on Windows as well. I heard the problem was due to Nvidia's graphics drivers being very resource intensive, but I'm not sure. I might be getting a new laptop or new laptop battery soon, so what can I do to increase the battery life so it doesn't wear away so quickly when running Linux? Thanks!

My first test with Ubuntu was to make my old ASUS UL30A dual boot and to test the battery run time.

Windows 7 lost, because it started SVCHOES.EXE using 100% of 1 from 2 CPUs.
Without this failure from Windows 7, the run time would be about equal.

But Windows always made failures like this, when I needed the longest possible battery run time.

I am now on a new Acer ES1-331-C0YK upgraded to 8 GB RAM and SSD. Just surfing, the system states typical below 5 Watt power usage. With dimmed display, even below 4 Watt are possible.

What states "Power Statistics" about Your battery and power usage?
At my 2010 ASUS UL30A, battery design 85 Wh, but only 67 Wh when fully charged.
At my new ACER ES1-331-C0YK battery design 36,7 Wh, but 37,4 Wh when fully charged.

Maybe Your battery lost much capacity.

Other typs: check with System Monitor, are all activities wanted?

---

