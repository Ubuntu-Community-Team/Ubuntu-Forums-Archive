---
title: "Pulseaudio not starting"
date: 2018-05-26
forum: General Help
---

### Post by ilpiero on 2018-05-26
Hello,

I have an asus e200HA, that because of the lacking of a kernel driver will start without audio interfaces.
Since version 18.04 when I open the volume control i get "estabilishing connection to pulseaudio, please wait..."

Eventually sometimes the volume control will open, but whet it does not it's impossible for instance to connect a bluetooth speaker since the pulseaudio daemon is not running.

What is preventing pulseaudio to start? Has anybody experienced this before?

syslog tells me the following

May 26 12:38:14 marco-E200HA pulseaudio[1470]: [pulseaudio] pid.c: Stale PID file, overwriting.
May 26 12:38:15 marco-E200HA pulseaudio[1470]: [pulseaudio] backend-ofono.c: Failed to register as a handsfree audio agent with ofono: org.freedesktop.DBus.Error.ServiceUnknown: The name org.ofono was not provided by any .service files

Thanks!

---

### Post by dkim-b on 2018-06-13
I'm running on Xubuntu 16.04 on kernel 4.4.0-128 and I have also been running into this issue. Unfortunately I don't know what causes the issue or how to fix it, but from a few tests of installing the OS from scratch, it seems like a package update has caused it.  I unfortunately don't know which package caused it yet.

---

