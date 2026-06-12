---
title: "Increasing battery life"
date: 2007-10-22
forum: General Help
---

### Post by chunchengch on 2007-10-22
I try to find effective measures to extend the battery life, and I found this thread [http://ubuntuforums.org/showthread.php?t=576855&highlight=battery+uptime](http://ubuntuforums.org/showthread.php?t=576855&highlight=battery+uptime),
in which, **aldeby** wrote "...tweak laptop-mode editing file /etc/laptop-mode/laptop-mode.conf

run lm-profiler to set unneded services to be automatically disabled when switching to battery mode
...",

however, I am still a Linux newbie and do not really know how/what to do, which service should be set to be disabled when switching to battery mode? 
what is the value after LM_PROFILER= for the service disabled?

Here are the snapshots of service-setting window, any help will be appreciated!

[ATTACH]47255[/ATTACH]    [ATTACH]47256[/ATTACH]

---

### Post by bobyy on 2007-10-22
Hy
First time to increase your battery life,set your Povernow or Cpufreq to powesave (this will scalle your processor to minium of 600mhz ) or Dynamic (this will allow your processor to to stay at 600 mhz and when it need`it to jump to higher frequency.) but i dont know what processor ypou have so i dont know if you will use Powernow or cpufreq ...powernow you can install with Synaptic...and ofcourse increas your brightness  on battery mode..
Good luck.

---

### Post by misfitpierce on 2007-10-22
terminal: gconf-editor

apps-gnome-power-settings-cpufreq

Change laptop mode to powersave.

:)

---

### Post by chunchengch on 2007-10-22
Thanks for quick reply!

> **misfitpierce said:**
> terminal: gconf-editor
apps-gnome-power-settings-cpufreq
Change laptop mode to powersave.
:)

I did it first, but nothing is changed, the power-management just shows the same message "the battery is fully charged and provides 1 hour and 55 minutes battery runtime". however, I check the battery information with hardinfo, the battery is charged only 86.63%.:(

[ATTACH]47294[/ATTACH]

> **bobyy said:**
> Hy
First time to increase your battery life,set your Povernow or Cpufreq to powesave (this will scalle your processor to minium of 600mhz ) or Dynamic (this will allow your processor to to stay at 600 mhz and when it need`it to jump to higher frequency.) but i dont know what processor ypou have so i dont know if you will use Powernow or cpufreq ...powernow you can install with Synaptic...and ofcourse increas your brightness  on battery mode..
Good luck.

powernowd is installed by default in Synaptic, however I find another package powersaved which is not installed, and when I click it to be installed, Synaptic will remove the powernowd, I don't know what the difference between powernowd and powersaved is, so I do nothing.

PS : I have a dual-core T2250 1.73GHz CPU of my ASUS F3Jc laptop

---

### Post by bobyy on 2007-10-22
so...
powersaved it is another utility ..another story :)

powernowd - it is just a daemon ..it is work wit cpu scalling programs.

my advise was related to POWERNOW..or CPU-freq ..this are 2 excelent utility for cpu scalling and reduce the energy consumption.

regards..

---

