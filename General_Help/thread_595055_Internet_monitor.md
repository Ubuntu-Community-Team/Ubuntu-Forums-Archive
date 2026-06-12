---
title: "Internet monitor?"
date: 2007-10-28
forum: General Help
---

### Post by FRuMMaGe on 2007-10-28
I am on an internet "budget" at the moment. If I download more than 6GB per month I will be charged extra by my service provider.

Is there a tool which will enable me to keep track of the exact amount I have downloaded?

---

### Post by Wiebelhaus on 2007-10-28
right click on taskbar and add to , Move system monitor to your task bar and then right click the monitor and select your options.

there's other more advanced ones but I like the simplistic nature of the inherent one and it works great so w/e , look at the top middle of my taskbar that's what it'll look like , and for a more advanced view of that one just click it.

And for how much which more applies to your question:

> apt-cache show ipband bandwidthd

[More about it:]("http://www.ubuntugeek.com/bandwidth-monitoring-tools-for-linux.html")

---

### Post by FRuMMaGe on 2007-10-28
> **sx66gns said:**
> right click on taskbar and add to , Move system monitor to your task bar and then right click the monitor and select your options.

there's other more advanced ones but I like the simplistic nature of the inherent one and it works great so w/e , look at the top middle of my taskbar that's what it'll look like , and for a more advanced view of that one just click it.

I already have system monitor set to Ctrl+Alt+Del (like windows :) )

Also, it only monitors it for that session. I was looking for something that would give me a running total for the month. I am using a laptop so I don't like to leave it on all the time.

---

### Post by rscott5 on 2007-10-28
There is a pretty cool program called bwm-ng that runs from the terminal. I'm not sure if it will do what you need but its worth checking out. You can find it in the Ubuntu repository.

---

### Post by evilregis on 2007-10-28
My dad had a virus-infected Windows PC that caused him to burn through his bandwidth for several months and caused him to have to pay more.

I'm setting him up with an Ubuntu machine and on it I've installed Darkstat.  You can get it in Synaptic.  It also has a web interface to view your traffic in the last 60 seconds, 60 minutes, day and month.

I had trouble getting it to run at startup even after editing the init.cfg file and had to resort to adding:

```
/etc/init.d/darkstat start
```

to my Startup Programs in System -> Appearance -> Sessions.

---

### Post by FRuMMaGe on 2007-10-28
> **evilregis said:**
> My dad had a virus-infected Windows PC that caused him to burn through his bandwidth for several months and caused him to have to pay more.

I'm setting him up with an Ubuntu machine and on it I've installed Darkstat.  You can get it in Synaptic.  It also has a web interface to view your traffic in the last 60 seconds, 60 minutes, day and month.

I had trouble getting it to run at startup even after editing the init.cfg file and had to resort to adding:

```
/etc/init.d/darkstat start
```

to my Startup Programs in System -> Appearance -> Sessions.

Sounds perfect. But when I installed it and ran it, I got this:

```
frummage@frummage-laptop:~$ darkstat
darkstat v2.6 using libpcap v2.4 (i486-pc-linux-gnu)
Error: pcap_lookupdev(): no suitable device found
frummage@frummage-laptop:~$

```

---

### Post by evilregis on 2007-10-28
Did you edit /etc/darkstat/init.cfg?

```
# You must set this option, else darkstat may not listen to
# the interface you want
INTERFACE="-i eth0"
```

It sounds like perhaps you're not using eth0 and need to change that to the proper interface.  Give that a check and see if that helps.

---

### Post by FRuMMaGe on 2007-10-28
Yeah i've sorted it.

It won't let me view the stats though, so now im using vnstat. It is just what I need

---

