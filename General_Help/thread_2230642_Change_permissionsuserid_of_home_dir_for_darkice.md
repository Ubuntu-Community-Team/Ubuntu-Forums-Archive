---
title: "Change permissions/userid of home dir for darkice"
date: 2014-06-20
forum: General Help
---

### Post by andrew-miller57 on 2014-06-20
I am having some issues with darkice starting and being able to stream for me.  I bevel that the issue may be related to permissions that somehow got changed and I think I need to change my home directory permissions back to my userid and group id...How would one go about doing this??  

All was working well yesterday and today it just stopped working...



```
andrew@andrew-server:~$ sudo darkice -c /etc/darkice.cfg DarkIce 1.0 live audio streamer, http://code.google.com/p/darkice/
Copyright (c) 2000-2007, Tyrell Hungary, http://tyrell.hu/
Copyright (c) 2008-2010, Akos Maroy and Rafael Diniz
This is free software, and you are welcome to redistribute it 
under the terms of The GNU General Public License version 3 or
any later version.


Using config file: /etc/darkice.cfg
Using ALSA DSP input device: default
Using POSIX real-time scheduling, priority 98
Home directory not accessible: Permission denied
ALSA lib pcm_dsnoop.c:618:(snd_pcm_dsnoop_open) unable to open slave
DarkIce: DarkIce.cpp:1187: can't open connector [0]



```

---

### Post by TheFu on 2014-06-20
sudo chown -R andrew.andrew ~/

---

