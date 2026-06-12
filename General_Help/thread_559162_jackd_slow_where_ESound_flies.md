---
title: "jackd slow where ESound flies"
date: 2007-09-24
forum: General Help
---

### Post by mdsxx on 2007-09-24
I'm trying to setup jackd in Feisty so that I can use it with Rosegarden and Timidity.

I've looked at other threads and wiki documentation (like Studio preparation) but
the best I've got is a WAV file being played at half speed (farmes/period =4096 and softmode).
(Tried many variations for all parameters in qjackctl).

What I don't understand is why (with the same hardware, CMI8738 onboard chip)
ESOund (esd) plays the same WAV file very well without losses or xruns...

Does jackd needs more resources than esd to playback a single file ?

And with same hardware I've also runned jack playing well (don't remender if it was
with Ubuntu 6.10 or Debian Sarge)...

Is there any untold way to get a single playback ?
(of course I've stopped esd before starting jackd)

Thanks in advance...

---

### Post by mdsxx on 2007-09-27
Trying both capture and playback seems to be taking double time to process...


.....
[FONT="Lucida Console"]delay of 23194.000 usecs exceeds estimated spare time of 11593.000; restart ...
delay of 23203.000 usecs exceeds estimated spare time of 11593.000; restart ...
delay of 23204.000 usecs exceeds estimated spare time of 11593.000; restart ...
delay of 23208.000 usecs exceeds estimated spare time of 11593.000; restart ...[/FONT]
             -------------                                                                  -------------
no message buffer overruns

By using just playback (-d alsa -d hw:0,1 -P) solves (while I don't be
needing capture) and keeps time 1:1 (playback/realtime).

---

