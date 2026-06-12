---
title: "Jack Audio Server"
date: 2008-04-24
forum: General Help
---

### Post by jonnodveidt on 2008-04-24
I have installed jackd package. JACK Control is under Sound&Video menu, but I can't start Jack server:

[I] jackd -R -d alsa
jackd 0.103.0
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details

JACK compiled with System V SHM support.
loading driver ..
creating alsa driver ... hw:0|hw:0|1024|2|48000|0|0|nomon|swmeter|-|32bit
control device hw:0
the playback device "hw:0" is already in use. Please stop the application using it and run JACK again
cannot load driver module alsa
no message buffer overruns[/I]

Any help here?

---

### Post by jhnphm on 2008-04-25
> **jonnodveidt said:**
> I have installed jackd package. JACK Control is under Sound&Video menu, but I can't start Jack server:

[I] jackd -R -d alsa
jackd 0.103.0
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details

JACK compiled with System V SHM support.
loading driver ..
creating alsa driver ... hw:0|hw:0|1024|2|48000|0|0|nomon|swmeter|-|32bit
control device hw:0
the playback device "hw:0" is already in use. Please stop the application using it and run JACK again
cannot load driver module alsa
no message buffer overruns[/I]

Any help here?

Run "pasuspender jackd -R -d alsa" to run jack, to temporarily disable pulseaudio.

Or just install and use qjackctl to run Jack, and it should suspend PA for you.

---

