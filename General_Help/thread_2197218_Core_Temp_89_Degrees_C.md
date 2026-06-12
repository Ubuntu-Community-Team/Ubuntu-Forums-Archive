---
title: "Core Temp 89 Degrees C"
date: 2014-01-02
forum: General Help
---

### Post by ishaan2 on 2014-01-02
My Ubuntu Desktop has a 6 Core AMD FX 6300 Processer and runs Ubuntu 13.04. Lately it has been shutting off like it has been unplugged randomly. So I installed lm_sensors. I checked the core temp it was 86 degrees and I kept checking every few seconds and it kept rising 1-2 degrees until it got to 89.7 degrees than shutoff. This started after I installed CPU Miner it is supposed to start when the computer starts up and I designated it to use 6 Cores. Does this have anything to do with it? What do I do to stop this from happening again?

---

### Post by QIII on 2014-01-02
Hello!

Have you physically inspected our cooling solution?  Is it a stock cooler?  In general a stock cooler will simply not be sufficient for a continuous heavy load on the CPU.

---

### Post by ishaan2 on 2014-01-02
It was a Custom Build

---

### Post by tgalati4 on 2014-01-02
Consumer-grade computers are not designed to mine bitcoin.  If you run all 6 cores at 100%, you will quickly wear out your motherboard.  You need to upgrade to server-grade hardware or get a better cooling system as QIII suggested.

---

### Post by ishaan2 on 2014-01-03
I switched it to 2 cores it now stays awake for about 10 minutes than shuts off. Even when I'm not running cpuminer. I have a thermaltakeusa power supply. It generally stayed around 59 to 63 degrees than started going up rapidly. I have one fan on my Proccesser how many fans should I have?

---

### Post by QIII on 2014-01-03
It's not as simple as a number of fans.

You need to get a baseline at idle.  Turn off your mining app altogether, don't run anything else and allow the machine to idle for about 30 minutes to get stable.  Check the temperature then and let us know what it is.

BTW -- is that fan actually running?

---

### Post by tgalati4 on 2014-01-03
It's time to clean off the old CPU heat paste and put some high-quality paste and take some measurements at idle and at load.  There are several youtube videos on how to do it.

---

### Post by ishaan2 on 2014-01-03
Yes fan is running. I put fancontrol on it says usr/sbin/fancontrol Invalid path to sensors how to I change this to /etc/modules where the sensors are? I have changed it to 0 cores and turned it off. I think I'll let it Idle. Now the temperature is going up about 1 degree every 2 minutes

---

### Post by QIII on 2014-01-03
You don't want to control the fan manually right now, so don't mess with fancontrol.  You need to see why your cooling system is not working.  Taking manual control of the fans will get in the way of that.

If your CPU keeps heating up while idling, there is something wrong.  Let's see what happens.  If it gets much above about 35 - 40 degrees as the raw reading from lm-sensors, you have a problem and you should turn your computer off.  I like to keep mine to no more than about 30 at idle.  AMDs return wonky values for temps, so I always add 8 - 10 degrees to what they are reporting through lm-sensors.  35 - 40 degrees is more likely 45 - 50 degrees and that is too hot at idle.

---

### Post by blinkydamo on 2014-01-03
You have to look at the cooling system itself.  You need to check that the cpu cooler is actually seated correctly on the cpu.  Check that the fan is blowing through the cooler and not drawing from the cooler.

Also what cooler is it? I know you have stated that it's a custom build but that just means someone built it for you, what components are used can vary a lot, is the cooler an aftermarket cooler or the stock one?

As stated running mining software will run you 6 cores flat out and generate a huge amount of heat, at the same time you will hardly be able to use your pc for anything else.  Also if you cpu temp is increasing when idle and getting hotter and hotter then you have a major heat issue, that needs solving.

Good luck,

Blinky

---

### Post by ishaan2 on 2014-01-03
Well now it stays at about 78 degrees now. Is that bad or good. lm_sensors reads that the fan is going at 3416 RPM. I switched cpuminer to one core and it doesn't seem to be causin problems.

---

### Post by deadflowr on 2014-01-03
78 degrees Celsius is hot no matter what. So, not good.
I'd follow the advice of cleaning and applying a new, better thermal paste and making sure the heatsink is properly seated nice and tight.
I'd also +1 running the system in idle, without cpuminer running at all, for at least half an hour and see what the temps are doing.

---

### Post by ishaan2 on 2014-01-03
I did that and it lingered around 78 degrees c

---

### Post by QIII on 2014-01-03
Bearing in mind that the temp returned by lm-sensors from AMD's odd thermistor is low, that is much too hot.  AMD CPUs shouldn't be taken above 60 degrees.  APUs run hotter, but not CPUs.  Don't run that machine.  You need to get a handle on your cooling.

---

### Post by tgalati4 on 2014-01-03
AMD's have a way of fixing themselves--poof.

---

### Post by deadflowr on 2014-01-03
> **tgalati4 said:**
> AMD's have a way of fixing themselves--poof.

Is that an Abracadabra poof, or a "Get outta the way, she's gonna blow!" poof?

---

### Post by tgalati4 on 2014-01-03
[Poof.]("http://www.youtube.com/watch?v=ssL1DA_K0sI")

---

### Post by pqwoerituytrueiwoq on 2014-01-03
What is your motherboard?
are you overclocking?
what case do you have? and are you using any extra fans in it
what is your power supply?
what is your CPU cooler?

that chip should not be getting that hot, maybe the sensor is wrong
89 F i could see as a idle temp, but not C the system would expect the system to cut it self off before it got that hot
if you are using a stock cpu cooler get a hyper 212 (budget cooler for moderate overclocking) or a NH-D14 (for serious overclocking)

---

### Post by soloman469 on 2014-01-03
> **tgalati4 said:**
> [Poof.]("http://www.youtube.com/watch?v=ssL1DA_K0sI")

You sir made my day! :grin: That not only made me ROFL but it also scared the hell out of me. XD

---

### Post by tgalati4 on 2014-01-03
That is one of several AMD self-destruction videos.  They also do the same type of torture testing on Intel CPU's and they halt quickly and survive to live another day.  So the message is don't mess around with AMD overheat issues.

---

### Post by ishaan2 on 2014-01-04
Temperature now lingers around 43 degrees celsuis. I have ordered fans off amazon. My processer only came with one fan and I only have one fan. How would the second fans get power

---

### Post by pqwoerituytrueiwoq on 2014-01-04
was not saying add fans to the cpu cooler, was saying replace the little dinky thing with a good cooler
[http://i.imgur.com/8Yz5B1b.jpg](http://i.imgur.com/8Yz5B1b.jpg) (case is a fractal define r4)
little dinky stock amd cooler (from 65W amd CPU) is on top of the case while the good cooler (cooler master hyper 212 evo) is on the CPU in the case
here is one with a nh-d14 in it
[http://i.imgur.com/W0bUOp2.jpg](http://i.imgur.com/W0bUOp2.jpg) (case is a fractal define XL)

edit:
BTW i have found that if you put a washer between the fan and the heat sync on the hyper 212 evo you get better temps (-3C on max load (4.2GHz@1.5125 vcore))

---

### Post by mc4man on 2014-01-04
From the bits & pieces I read over time about bitcoin can't see that cpu mining will ever produce more than it's cost.
(maybe you feel differently but myself wouldn't bother..

---

### Post by deadflowr on 2014-01-04
> **ishaan2 said:**
> Temperature now lingers around 43 degrees celsuis. I have ordered fans off amazon. My processer only came with one fan and I only have one fan. How would the second fans get power

As stated you only need one cpu fan/cooling apparatus.
But you can add multiple case fans, which will pull that excess hot air out of the box faster, helping keep the machine's innards cooler.
Most mobo's have extra sockets for case fans, or the like.
As asked before, what's the motherboard?
Worst case(pun!), you can always power the extra fans directly from the power supply unit(PSU)
You would need an adapter plug for that, though.

---

### Post by pqwoerituytrueiwoq on 2014-01-04
> **deadflowr said:**
> Worst case(pun!), you can always power the extra fans directly from the power supply unit(PSU)
You would need an adapter plug for that, though.not if you have a soldering iron, solder, electrical tape, and wire strippers
on the molex connector the yellow is 12v this goes to the fans's red wire for 100% fan speed the black wire next to the yellow wire goes to the black wire on the fan
if you use the red wire on the molex connector and the black cable next to that one you will get 5v (most fans will run with 5v)
if you use the red wire and the yellow wire (yellow to red and red to black) you will have 7v power on the fan, almost every fan will run on 7v

most fans (every retail fan i ever saw) comes with a adapter

---

### Post by mcduck on 2014-01-05
> **tgalati4 said:**
> That is one of several AMD self-destruction videos.  They also do the same type of torture testing on Intel CPU's and they halt quickly and survive to live another day.  So the message is don't mess around with AMD overheat issues.

Of course the video *is* made with ages old Duron CPU (from over 10 years ago), which didn't have any kind of thermal throttling or overheating protection like any modern CPU does... ;) So probably not a good example of how a current-day AMD CPU would deal with lack of cooling. :D

Anyway, even the stock cooler, when attached correctly, should be able to keep the idle temperature fairly close to room temperature, so if the idle temp is hight adding new fans is probably not the correct way to go, checking that the heatsink is attached properly and has correct amount of decent quality thermal paste would be the way to go. (And of course making sure the case itself has some airflow)

---

