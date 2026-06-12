---
title: "Dell laptop fan control issue - dell-smm-hwmon"
date: 2016-04-07
forum: General Help
---

### Post by quert on 2016-04-07
Hi all,
during last week I have tried to install Xubuntu 14.04 LTS and Ubuntu Mate 15.04 on my Dell Studio 1537. I had no issues with wmi and function keys, bluetooth and wireless, graphics.

But one thing that I wanted to tweak was fan speed. I tried fancontrol/pwmconfig and i8kutils. When used pwmconfig controls fan speed via hwmon device and reads/writes speed. It seems that there is some problem as whenever any programm was reading/writing pwm/speed laptop hangs for 1-5 seconds.

I discovered this hard way when tried to run xsensors and barely could shut it down as there is no other activity during this pauses and xsensors polls sensors quite often. The same issue seems to be with i8kutils - when run, polling/writing hwmon pwm and input from speed makes system unworkable.

I narrowed it down to dell-smm-hwmon kernel module and after blacklisting, polling sensors (with sensors or xsensors) works normally. But the catch is that without dell-smm-hwmon I get no pwm control device for fan so, cannot read or change fan speed.

Here is described similar issue [https://bbs.archlinux.org/viewtopic.php?id=203488]("https://bbs.archlinux.org/viewtopic.php?id=203488")

It seems that dell-smm-hwmon could be not used if there was driver for ITE ITE8512E/F/G as sensor-detect finds it. It seems that it could controll and read fan speed, but it is not implemented (lm-sensors site seems to be down @writing time)

Does anyone have and idea how to tackle this dell-smm-hwmon?

@fast edit
I have chceked this on BIOS'es:  A11, A09, A08
and kernels: 3.19.8, 4.20, 4.3.6

---

