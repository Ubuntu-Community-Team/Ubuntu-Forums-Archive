---
title: "How to configure battery info path to acpi?"
date: 2006-12-09
forum: General Help
---

### Post by jrvwagner on 2006-12-09
My battery info is on /proc/acpi/battery/CMB0 not in /proc/acpi/battery/BAT0. Power Management is not founding the info and thinks my batery is empty.
I tried to create a symbolic link but I cannot do it in /proc
Where do I configure the correct path for acpi?
Thanks.
Jose Roberto

---

### Post by soumyadc on 2006-12-11
I also have a similar like problem. I am using ubuntu on acer 4020 travelmate laptop.
THe icon in the taskbar is not showing the proper battery status.Its always showing
"System is running on AC power
 Battery charged (0%)"

This icon and information doesnot change if I plugged in or out the power cable.


My battery related files are present at
/proc/acpi/battery/BAT1 directory

#ls
alarm  info  state
# cat alarm
alarm:                   unsupported

# cat info
present:                 yes
design capacity:         2200 mAh
last full capacity:      1880 mAh
battery technology:      rechargeable
design voltage:          14400 mV
design capacity warning: 300 mAh
design capacity low:     132 mAh
capacity granularity 1:  32 mAh
capacity granularity 2:  32 mAh
model number:            ZL03
serial number:           25755
battery type:            LION
OEM info:                11

# cat state
present:                 yes
ERROR: Unable to read battery status

---

### Post by jrvwagner on 2006-12-11
I have changed the Power Manager for Klaptopdaemon and now my battery info is showing right.

I don't know if there is a similar program in Gnome.

Check your repository and try others programs for battery info, in my case it worked.

---

### Post by soumyadc on 2006-12-11
Ahh! that is most junky way to searching for a tool that may or may not work. I want to know the actual configurations and modifications need to be done through command line itself. If anybody knows about this please help me out.

---

### Post by jasin on 2007-01-12
I am having the same problem guys. There must be a way to fix this!

---

### Post by mbc2000 on 2007-05-05
Has anyone figured this out yet?  My laptop has CMB0, too.  klaptop works fine, but gnome-power-mananger reports "0%".  I prefer Ubuntu to Kubuntu on this laptop.

I unplugged my AC adapter and did a 'cat state' on /proc/acpi/battery/CMB0:

[FONT="Courier New"]present:                 yes
capacity state:          ok
charging state:          discharging
present rate:            977 mW
remaining capacity:      3512 mWh
present voltage:         16306 mV[/FONT]

I plugged the AC adapter back in:

[FONT="Courier New"]present:                 yes
capacity state:          ok
charging state:          charging
present rate:            977 mW
remaining capacity:      3465 mWh
present voltage:         16275 mV[/FONT]

This looks like good info to me.  Why can't gnome-power-manager use it?

---

### Post by Luis Marks on 2007-05-08
In my Compaq Evo notebook i have the same error. The Gnome Power Manager don't show the battery status...

---

