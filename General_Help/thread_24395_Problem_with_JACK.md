---
title: "Problem with JACK"
date: 2005-04-06
forum: General Help
---

### Post by cyberloon on 2005-04-06
I'm trying to start jack under the current version of Hoary, but it stalls. My console looks like this when I try:

```
cyberloon@Istari:~ $ jackd -d alsa
jackd 0.99.0
Copyright 2001-2003 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details

loading driver ..
creating alsa driver ... hw:0|hw:0|1024|2|48000|0|0|nomon|swmeter|-|32bit
control device hw:0
configuring for 48000Hz, period = 1024 frames, buffer = 2 periods
Couldn't open hw:0 for 32bit samples trying 24bit instead
Couldn't open hw:0 for 24bit samples trying 16bit instead


```

Then it just stops, very similar things happen when I try it with oss. I know that alsa and oss both work, because when I try using Hydrogen or XMMS it plays excellently.
I of course begin by running
```
sudo killall esd
```

---

### Post by nicholaspaul on 2005-04-07
I have an answer, which has kind of helped my problems, but I don't know enough about Ubuntu to know if its a complete answer (how about that for a caveat!) 

The Rosegarden tutorial is very noobie friendly - [http://rosegarden.sourceforge.net/tutorial/using-rosegarden/en/chapter-2.html](http://rosegarden.sourceforge.net/tutorial/using-rosegarden/en/chapter-2.html)

About 3/4 the way down is a section on JACK: I installed qjackctl . Very helpful. Not perfect, but I"m closer to getting a DAW working! 

Installing gnome-alsamixer was helpful too. I had stuff turned off that stopped my audio working. 

Both of these are available from Synaptic.

---

