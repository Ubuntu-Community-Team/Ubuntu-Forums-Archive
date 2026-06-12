---
title: "network ups monitor packages problem"
date: 2008-05-04
forum: General Help
---

### Post by weltall2 on 2008-05-04
It seems ubuntu packages (which now are supported packages by core developers and in the main repositories) for network ups monitor are lacking an additional package or doesn't take care of a configuration which should be quite normal for something like network ups monitor.
As you know NUT is a driver/server/client implementation with separated parts. But ubuntu packages takes for granted that all of those must be in the local machine, so the ups must be also connected to the local machine.
A great feature of NUT is the capability of connecting the ups to a machine (in my case one who uses way less power than most computers i've here... less than 20W) and being able to dispatch informations about the ups status to the entire network (and even externally the network). This makes really usefull setupping one machine as a server and all the others as clients (with just upsmon running)

And this is the problem there is no support for the so called in nut slave configuration. The init scripts WANTS to load also usdrvctl and upsd else it doesn't load upsmon.
This is a big blocker for NUT which should be fixed by an additional package for slave configurations with a proper init script or the possibility to load upsmon also if upsd and upsdrvctl failed loading.

i've also opened a bug report:
[https://bugs.launchpad.net/ubuntu/+source/nut/+bug/226405](https://bugs.launchpad.net/ubuntu/+source/nut/+bug/226405)

thanks for the help

---

