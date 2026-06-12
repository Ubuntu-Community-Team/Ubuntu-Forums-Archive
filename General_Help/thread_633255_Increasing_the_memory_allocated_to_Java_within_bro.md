---
title: "Increasing the memory allocated to Java within browser-based applets"
date: 2007-12-06
forum: General Help
---

### Post by TheFuzzy0ne on 2007-12-06
Hi everyone.

I play an online Java applet-based game, and it crashes quite often.

I've done some looking around into what the possible causes could be, and the most likely would be that there is not enough RAM being allocated to the JVM at runtime. :-k

I've done [this]("http://www.fsoft.it/temp/memorytest.htm") test several times, and each time the results show that only 59MB of RAM could be allocated.

I have been playing with "JControl", which I believe is Sun Microsystems own creation(?), and trying to feed it different parameters in the "Java Applet Runtime Settings" view, under the "Java" tab.

So far, I have added the following combinations (and tested it after each application of the parameters), to no avail: ](*,)

-Xmx256m
-Xms256m
-Xmx256m -Xms256m
-VMArgs "-Xmx256m -Xms256m"
-VMArgs -Xmx2506m -Xms2506m

To be honest, I'm not entirely sure of the format required for the parameters, which is why I tried the above combinations. I've rummaged through loads of documentation, and quite frankly I'm surprised that Google haven't banned me for doubling their server load... :shock:

I know how to create a shortcut which passes parameters onto the JVM at runtime, but I can't figure out what I need to do in order to allocate 256MB of RAM to browser applets. :confused:

I am running the latest Java version:

java version "1.6.0_03"
Java(TM) SE Runtime Environment (build 1.6.0_03-b05)
Java HotSpot(TM) Client VM (build 1.6.0_03-b05, mixed mode, sharing)

and I have 2.5GB of system RAM.

I would really appreciate it if anyone can tell me where the file I need to tweak is before I pull out what little remaining hair I have. :mad:

Many, many thanks in advance. [-o<

Daz.

---

### Post by TheFuzzy0ne on 2007-12-08
*Bump*

---

### Post by TheFuzzy0ne on 2007-12-17
*Bump* (Surely someone out there can offer some advice, please.)

---

