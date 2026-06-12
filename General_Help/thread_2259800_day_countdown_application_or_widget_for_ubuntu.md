---
title: "day countdown application or widget for ubuntu"
date: 2015-01-07
forum: General Help
---

### Post by IAMTubby on 2015-01-07
Is there any application which counts days leading to an event? Like I set a day D and it counts days until day D.
Something like [this]("http://www.timeanddate.com/countdown/generic?iso=20150316T00&p0=43") one, but this is a web app, I was looking for a desktop widget

---

### Post by slickymaster on 2015-01-07
There's Alarm Clock for GNOME ```
sudo apt-get install alarm-clock-applet
```It is easy to use with support for multiple and repeatable alarms, as well as snoozing and a flexible notification system. Two types of alarms are supported: Alarm Clocks and Timers. Notification is done by either playing a sound or launching an application.

---

### Post by IAMTubby on 2015-01-07
> **slickymaster said:**
> There's Alarm Clock for GNOME ```
sudo apt-get install alarm-clock-applet
```It is easy to use with support for multiple and repeatable alarms, as well as snoozing and a flexible notification system. Two types of alarms are supported: Alarm Clocks and Timers. Notification is done by either playing a sound or launching an application.
Thanks for the reply, I did try and install it. But does it have an option to set the number of days? I just see boxes for hours, minutes and seconds.
What I would like is just a countdown of days alone upto February 1, say .

---

### Post by slickymaster on 2015-01-07
```
~$ apt-cache search timer | grep clock
alarm-clock-applet - Alarm Clock applet
**[COLOR=#ff0000]gnome-clocks - Simple GNOME app with stopwatch, timer, and world clock support[/COLOR]**
libboost-timer-dev - C++ wall clock and CPU process timers (default version)
libboost-timer1.54-dev - C++ wall clock and CPU process timers
libboost-timer1.54.0 - C++ wall clock and CPU process timers
libboost-timer1.55-dev - C++ wall clock and CPU process timers
libboost-timer1.55.0 - C++ wall clock and CPU process timers
libghc-clock-dev - High-resolution clock and timer
libghc-clock-doc - High-resolution clock and timer; documentation
libghc-clock-prof - High-resolution clock and timer; profiling libraries
libghc-clocked-dev - timer functionality to clock IO commands
libghc-clocked-doc - timer functionality to clock IO commands; documentation
libghc-clocked-prof - timer functionality to clock IO commands; profiling libraries
twclock - World clock for ham radio operators
wmclockmon - Displays a clock in 12/24h mode with alarm mode
```

Not sure if it fits your requirements but it's worth to try gnome-clocks.

---

### Post by Habitual on 2015-01-07
> **slickymaster said:**
> Not sure if it fits your requirements but it's worth to try gnome-clocks.
Should be noted that there is no "days" in the timer,
and manual settings only go to 99:99:99

---

### Post by slickymaster on 2015-01-07
> **Habitual said:**
> Should be noted that there is no "days" in the timer,
and manual settings only go to 99:99:99

Wasn't aware of that as I never used it, but thanks for the heads up.

---

### Post by IAMTubby on 2015-01-07
> **Habitual said:**
> Should be noted that there is no "days" in the timer,
and manual settings only go to 99:99:99

> **slickymaster said:**
> 
Not sure if it fits your requirements but it's worth to try gnome-clocks.

I was actually looking for something which counts days.

Actually, we don't have to think of it as days/hours/minutes etc, I just need a number going in reverse until 0.

---

### Post by Habitual on 2015-01-07
gnome-shell-timer ?

---

### Post by slickymaster on 2015-01-07
[https://github.com/olebowle/gnome-shell-timer](https://github.com/olebowle/gnome-shell-timer)

_EDIT:_ Habitual beat me

---

### Post by CantankRus on 2015-01-07
I have attached a conky that uses a python script to countdown in days to go
to any date you specify.
Extract the downloaded archive and and view the included readme.txt for instructions.

You will need to install conky...
```
sudo apt-get install conky
```

---

### Post by tgalati4 on 2015-01-07
Days until Christmas 2015:

```
echo \(`date -d '2015-12-25' +%s`-`date +%s`\)/86400 | bc
```

Now I need to figure out how to display in a panel.

---

