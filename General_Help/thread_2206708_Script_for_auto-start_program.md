---
title: "Script for auto-start program"
date: 2014-02-20
forum: General Help
---

### Post by cy1on on 2014-02-20
I've downloaded cpu-freq program that is placed on the top bar. I have to start this program by typing indicator-freq in the Terminal. But when I close Terminal the program shuts off. How do I create a shell script or something so it will automatically start when the computer starts?

---

### Post by ajgreeny on 2014-02-20
What OS are you using as that will affect what you need to do to get the application/utility to autostart?

It may not need a script to start it as you may be able to simly add the command **indicator-freq** to the autostart listing, but we need to know the OS.

---

### Post by cy1on on 2014-02-20
I'm using 13.10.

---

### Post by stevephillipgreen on 2014-02-20
I'm using 13.10 as well, it always autoruns for me. Once started the 1st time from the terminal (the indicator appears near the clock), the next time you reboot it should run automatically.

This is via software centre install. I've never manually installed it so that may be different.

It's actually indicator-cpufreq that you run, you have put indicator-freq. Perhaps a typo?

---

### Post by cy1on on 2014-02-20
Hmm, wierd. I've downloaded this: [https://launchpad.net/indicator-cpufreq](https://launchpad.net/indicator-cpufreq) and installed by apt-get and i tried removing it and installed it via Software Center, but the same problem exists. I saw a comment that another user was experiencing this.

---

### Post by stevephillipgreen on 2014-02-20
Okay.. in which case open startup applications and add it like so..

CPU Frequency Scaling Indicator

indicator-cpufreq

An indicator for monitoring and switching CPU frequency scaling

[IMG]http://dl.dropbox.com/u/2528687/Edit%20Startup%20Program_067.png[/IMG]

---

