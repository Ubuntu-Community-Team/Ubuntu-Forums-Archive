---
title: "jackd error while trying to start ardour/ardour2"
date: 2007-05-08
forum: General Help
---

### Post by vav on 2007-05-08
I wanted to do some wave file editing in linux, so I installed ubuntustudio-audio, and tried running ardour-gtk, but got the error:
```

jackstart: md5 checksum for /usr/bin/jackd does not match

```
How do I solve this? I've also tried getting ardour2 from [www.getadeb.net](www.getadeb.net), installed that after removing ardour-gtk and it gives the same error. Of course jack did not get upgraded.

How do I solve this?

---

### Post by christhemonkey on 2007-05-08
Why are using jackstart?
From its manpage:
> The jackstart command provides JACK's built-in support for Linux 2.4.x kernels with the realtime capabilities patch

Try just running from a terminal:
```
jackd -R -d alsa -d hw:0 
``` And posting the output here.

---

### Post by vav on 2007-05-08
Here's the output:

```

jackd 0.102.20
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details

JACK compiled with System V SHM support.
cannot use real-time scheduling (FIFO at priority 10) [for thread -1210446976, from thread -1210446976] (1: Operation not permitted)
cannot create engine

```

I'm not using jackstart... ardour starts it automatically. I dont need to do any real-time sound recording or editing, so I just have the standard kernel... is there a way of telling jack/ardour this?

---

### Post by christhemonkey on 2007-05-09
When starting jackd from the terminal, dont use the flag -R (like i suggested, sorry, i am too used to using realtime)
```
jackd -d alsa -d hw:0 
```

Also you might want to install qjackctl, it provides a nice GUI interface to jack and jack connections.

---

### Post by vav on 2007-05-10
Thanks that worked. My synaptic says qjackctl is installed...

---

### Post by christhemonkey on 2007-05-11
Well if its installed, then launch it from the menu then! :D

Applications > Sound & Video > Jack Control (or something like that, might just be qjackctl)

---

