---
title: "Reduced Battery life after installing Ubuntu"
date: 2007-06-10
forum: General Help
---

### Post by grathinam on 2007-06-10
HI

After installing Ubuntu, my battery lost only for about 30 minutes, any idea what I have to do to resolve this, precisely before installing Ubuntu I use to get 3.5 hours of battery life.

Make and Model

IBM T 41P

Thanks in advance

---

### Post by scrooge_74 on 2007-06-10
Start by giving make and model of your laptop, probably someone here has the same one and knows the ansewr

---

### Post by jrusso2 on 2007-06-10
Linux power management has never been as good as windows.  You might be able to make up some of it by playing with power management settings.

---

### Post by trippinnik on 2007-06-10
First there's a great Wiki aimed at the many Thinkpad users out there: [http://www.thinkwiki.org/wiki/ThinkWiki](http://www.thinkwiki.org/wiki/ThinkWiki) and  there's also a great (new) utility from Intel [http://www.linuxpowertop.org/](http://www.linuxpowertop.org/) that shows you what processes are sucking down too much power.  Unfortunately thinkpad extras module is one of them.  You'll also need one of the 2.6.22 tickless kernels and the module to get powertop to work.  The new tickless kernels should help reduce your battery usage as well.  Unfortunately you'll need to build your own kernel until there is an official update.  There are a few guides around on how to do it.

---

### Post by 444 on 2007-06-10
Two main things:
Make sure Cpufreq (Speedstep) is working, eg right-click the Gnome panel and add the CPU Frequency monitor to it to see what speed you're at... should be 600mhz, not maximum speed.

Install ATI drivers and enable PowerPlay.

---

