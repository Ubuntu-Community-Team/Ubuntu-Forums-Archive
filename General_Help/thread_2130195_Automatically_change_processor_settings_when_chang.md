---
title: "Automatically change processor settings when changing to/from battery on laptop"
date: 2013-03-28
forum: General Help
---

### Post by nmyrick on 2013-03-28
Does anyone know how I would write a script that would automatically change my processor settings to conservative when switching to battery, and back to performance when switching to A/C?

I am running Ubuntu 10.04 and I already have my processors set to performance by default.

Thanks,

Neil

---

### Post by erind on 2013-03-30
If you're using a command-line tool, such as **cpufreq-set**, to set manually the laptop's performance/conservative modes, then it's not that hard to implement such a script. If so, post that command(s) and the output of these commands:

```
find /proc/acpi/battery/ -ls

find /sys/class/power_supply/

ls -l /sys/class/power_supply/AC0/online
```
Otherwise if you're using a GUI tool, it might not be that trivial, at least from my viewpoint.

---

### Post by nmyrick on 2013-03-30
> **erind said:**
> If you're using a command-line tool, such as **cpufreq-set**, to set manually the laptop's performance/conservative modes, then it's not that hard to implement such a script. If so, post that command(s) and the output of these commands:

```
find /proc/acpi/battery/ -ls

find /sys/class/power_supply/

ls -l /sys/class/power_supply/AC0/online
```
Otherwise if you're using a GUI tool, it might not be that trivial, at least from my viewpoint.

Here is the output of those commands:

*******@Aquarius:~$ find /proc/acpi/battery/ -ls
4026532068    0 dr-xr-xr-x   3 root     root            0 Mar 30 20:35 /proc/acpi/battery/
4026532069    0 dr-xr-xr-x   2 root     root            0 Mar 30 20:35 /proc/acpi/battery/BAT1
4026532072    0 -rw-r--r--   1 root     root            0 Mar 30 20:35 /proc/acpi/battery/BAT1/alarm
4026532071    0 -r--r--r--   1 root     root            0 Mar 30 20:35 /proc/acpi/battery/BAT1/state
4026532070    0 -r--r--r--   1 root     root            0 Mar 30 20:35 /proc/acpi/battery/BAT1/info
*******@Aquarius:~$ find /sys/class/power_supply/
/sys/class/power_supply/
/sys/class/power_supply/ACAD
/sys/class/power_supply/BAT1
*******@Aquarius:~$ ls -l /sys/class/power_supply/AC0/online
ls: cannot access /sys/class/power_supply/AC0/online: No such file or directory
*******@Aquarius:~$ 

Right now, I use CPU Frequency Scaling Monitor 2.30.0 in the gnome panel to adjust the frequency manually.  I am running Ubuntu 10.04.

Thanks,
Neil

---

### Post by erind on 2013-03-30
It seems that **online** file is under ACAD directory. Can you run:

```
cat /sys/class/power_supply/ACAD/online

```
Also in my script I use **inotifywait** and **cpufreq-set**, so just to make sure they are installed, run:

```
which inotifywait

which cpufreq-set

```
I'm gonna need the above output to modify the script.

---

### Post by zombifier25 on 2013-03-31
There's an applet called Jupiter that automatically adjust settings like CPU, brightness, etc if you're on battery or on AC in order to conserve energy: [http://jupiter.sourceforge.net/index.html](http://jupiter.sourceforge.net/index.html)

---

### Post by 3rdalbum on 2013-03-31
OnDemand is usually the best CPU governor. Your CPU sleeps when there is nothing to do, then runs slowly when there is only a small load. When there is a large load, the CPU sprints, and then when the load drops it immediately goes back to sleep.

Intel says it is more power efficient to run the CPU fast and complete its work quickly and make it sleep sooner, than it is to run it for longer at a slow pace. Intel also says that the performance gain by using the Performance governor (basically running the CPU at full speed all the time) is nearly immeasurably low.

I don't know what software can change the governor on AC or battery (you could write a simple Bash script maybe?) but from what I understand your idea will hinder battery life, lower performance on battery and not help performance on mains power.

---

### Post by Linuxisfast on 2013-03-31
TLP from [www.linrunner.de](www.linrunner.de) does that and more to save power, my power consumption with Ubuntu 12.04x64 went from 14W idle to 8W on my ASUS laptop with TLP installed and running on battery.

---

