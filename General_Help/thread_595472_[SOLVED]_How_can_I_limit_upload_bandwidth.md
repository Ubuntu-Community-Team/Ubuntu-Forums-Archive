---
title: "[SOLVED] How can I limit upload bandwidth?"
date: 2007-10-28
forum: General Help
---

### Post by viciouslime on 2007-10-28
Does anyone know how I can limit my Ubuntu machine so that it will never upload faster than 20kbps. Preferably only on connections across the web, but if I have to I could limit it so that all network traffic is limited to 20kbps upstream.

---

### Post by dacap06 on 2007-10-28
What you are asking about is called traffic shaping.  This capability used to be a black art involving kernel settings and sacrificial chickens, but  recently it has become much easier.  Take a look at the Shaper package.  It contains an init script that runs at startup, and it should do exactly what you want.  Here's an excerpt from the package explanation:

This init script sets up traffic shaping using Linux's class-based queueing. This can be used to build smart bandwidth shapers which understand TCP/IP. See /usr/share/doc/shaper/README.shaper.gz for more details.

---

### Post by viciouslime on 2007-10-29
> **dacap06 said:**
> What you are asking about is called traffic shaping.  This capability used to be a black art involving kernel settings and sacrificial chickens, but  recently it has become much easier.  Take a look at the Shaper package.  It contains an init script that runs at startup, and it should do exactly what you want.  Here's an excerpt from the package explanation:

This init script sets up traffic shaping using Linux's class-based queueing. This can be used to build smart bandwidth shapers which understand TCP/IP. See /usr/share/doc/shaper/README.shaper.gz for more details.

Thank you very much for this witty and extremely useful response! I will try it out ASAP :D

---

### Post by viciouslime on 2007-10-29
Well I have got so far, but I am very stuck with the config file. I have read the documentation and come up with the following:

```
DEVICE=eth0,100Mbit,10Mbit
RATE=20Kbit
WEIGHT=2Kbit
RULE=192.168.1.2
```

However that gives me this:

```
sudo /etc/init.d/shaper restart
Stopping CBQ traffic shaping: shaper.
Starting CBQ traffic shaping: find: warning: you have specified the -maxdepth option after a non-option argument (, but options are not positional (-maxdepth affects tests specified before it as well as those specified after it).  Please specify options before other arguments.

find: warning: you have specified the -maxdepth option after a non-option argument (, but options are not positional (-maxdepth affects tests specified before it as well as those specified after it).  Please specify options before other arguments.

RTNETLINK answers: No such file or directory
shaper.
```

Anyone know anything more about this?

---

### Post by viciouslime on 2007-11-17
Just for anyone else that needs this, my solution so far is as follows:

```
sudo tc qdisc add dev eth0 root tbf rate 176kbit latency 50ms burst 1540

```

If this produces the following output:

```
RTNETLINK answers: File exists

```

Then use this instead:
```
sudo tc qdisc replace dev eth0 root tbf rate 176kbit latency 50ms burst 1540
```

Replace eth0 in all cases with the card you wish to limit the upload rate of. At present this will limit the rate of ALL traffic, I am working on getting it to limit only external traffic and will post something more comprehensive once I have done this. :)

---

### Post by gmaniac on 2007-11-17
cool! :cool:
It would be great if you could explain the options used or are available, like a
mini howto. If you had the time of course ;)
thnx anyways.

---

### Post by ramkumail on 2007-11-17
I second the request. I am a new user and it will be very useful and intersting if i can limit my upload speed.

---

### Post by tehet on 2007-11-17
> **viciouslime said:**
> I am working on getting it to limit only external traffic and will post something more comprehensive once I have done this. :)
That'd be great!

One thing though
> Then use this instead:
is identical to the first line you suggested. Anywho, I'll bookmark this :)

---

### Post by viciouslime on 2007-11-18
> **tehet said:**
> That'd be great!

One thing though

is identical to the first line you suggested. Anywho, I'll bookmark this :)

Lol oops, corrected that now. I will write up a proper howto at some point, explaining how it all works, for now though i'm really busy. In a few weeks! :)

---

### Post by Mithrilhall on 2007-11-19
[www.mastershaper.org](www.mastershaper.org)

---

### Post by viciouslime on 2007-11-20
> **Mithrilhall said:**
> [www.mastershaper.org](www.mastershaper.org)

That's fantastic!!! Thank you so much! :)

---

