---
title: "Wi-fi is disabled by hardware switch, hard blocked: yes"
date: 2015-01-28
forum: General Help
---

### Post by zenbenhoboe.com on 2015-01-28
I run Ubuntu 14.04 on a Lenovo Thinkpad T500. Wi-fi ran great until today. I cannot turn on wi-fi, which says "wifi is disabled by hardware switch."
The only thing that changed was that I had run apt-get instal flashplugin-installer and apt-get install pipelight-multi in an attempt to get sites like Netflix, HBOgo and Showtime Anytime to work, which incidentally did nothing to help me get video play.on those sites.
Anyway, today I turned on computer and found my wifi disabled.
I ran remove, purge and autoremove on both flashplugin and pipelight, hoping it would undo whatever hardware switch they had caused but to no avail.
I've searched for solutions but found none working for me.
Any advice?

---

### Post by zenbenhoboe.com on 2015-01-28
Wireless is enabled in BIOS.

---

### Post by grounds on 2015-01-28
give this a shot:

> sudo rfkill unblock wifi

---

### Post by zenbenhoboe.com on 2015-01-29
No go.

---

### Post by Pilot6 on 2015-01-29
Try

sudo modprobe -r ideapad_laptop

---

### Post by zenbenhoboe.com on 2015-01-29
No go.

---

### Post by Penguin360 on 2015-01-29
Try:
1. Update network adapter driver, if this does not help, then
2. Go to BIOS, then load the default settings of BIOS.

---

### Post by zenbenhoboe.com on 2015-01-29
How do I update network adapter driver?

---

### Post by Penguin360 on 2015-01-29
It does not seem Levono has a Linux driver for the network card, so you best bet will be: System Settings->Software & Updates->Additional Drivers

If this is not working, then try loading the default settings of your BIOS.

---

### Post by zenbenhoboe.com on 2015-01-29
OK there is nothing in additional drivers. 
Keep in mind, I can't get online because my wifi is disabled and I hotspot off of my phone.
The proper driver has to be somewhere, because the computer worked fine for several weeks since I bought it, before wifi became disabled in the last few days after I installed Chrome, Pipelight, and Flash.
I've since removed all three, but whatever change was made that caused my wifi to be disabled because of hardware switch, is still in effect.

---

### Post by zenbenhoboe.com on 2015-01-29
Default settings in BIOS  doesn't do anything.

---

### Post by zenbenhoboe.com on 2015-01-29
Is there a way to revert back to OS as it was several days ago?

---

### Post by zenbenhoboe.com on 2015-01-29
Omg duh, I'm so sorry to waste my own time and anybody's. Despite having read that there may be a switch on the side of the laptop, and despite having looked and not found one, I have found that there is indeed a switch, on the front, which I mistook as the same switch that locks/unlocks the laptop closed/opened.
Wifi working fine now. Duh to me.

---

### Post by Penguin360 on 2015-01-29
> **zenbenhoboe.com said:**
> Omg duh, I'm so sorry to waste my own time and anybody's. Despite having read that there may be a switch on the side of the laptop, and despite having looked and not found one, I have found that there is indeed a switch, on the front, which I mistook as the same switch that locks/unlocks the laptop closed/opened.
Wifi working fine now. Duh to me.

Not a problem, this happens. Cheers!

BTW, you may want to mark your question RESOLVED.

---

