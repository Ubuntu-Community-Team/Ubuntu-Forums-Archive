---
title: "Ubuntu resert sound configuration"
date: 2013-04-05
forum: General Help
---

### Post by ddz0703 on 2013-04-05
Hello community i have the next problem
On Ubuntu 12.04 i got a 5.1 sound system. I can configure that from the panel just like the next picture

[http://oi50.tinypic.com/2hxvtc.jpg](http://oi50.tinypic.com/2hxvtc.jpg)

and when i play a audio file, this sounds good like the configuration wished. But the problem is in the moment that the player change a song,
this change the sound configuration like Stereo 2.0 and i have to change it from the panel again.

I've seen in the panel the next sequence:

[http://oi50.tinypic.com/2hxvtc.jpg](http://oi50.tinypic.com/2hxvtc.jpg)
[http://oi48.tinypic.com/smynp3.jpg](http://oi48.tinypic.com/smynp3.jpg)
[http://oi45.tinypic.com/1z6wsaw.jpg](http://oi45.tinypic.com/1z6wsaw.jpg)

when i change the sound device, and return to analog, this is reseted on Stereo
this is my /etc/pulse/demon.conf

[B]# This file is part of PulseAudio.
#
# PulseAudio is free software; you can redistribute it and/or modify
# it under the terms of the GNU Lesser General Public License as published by
# the Free Software Foundation; either version 2 of the License, or
# (at your option) any later version.
#
# PulseAudio is distributed in the hope that it will be useful, but
# WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the GNU
# General Public License for more details.
#
# You should have received a copy of the GNU Lesser General Public License
# along with PulseAudio; if not, write to the Free Software
# Foundation, Inc., 59 Temple Place, Suite 330, Boston, MA 02111-1307
# USA.

## Configuration file for the PulseAudio daemon. See pulse-daemon.conf(5) for
## more information. Default values are commented out. Use either ; or # for
## commenting.

; daemonize = no
; fail = yes
; allow-module-loading = yes
; allow-exit = yes
; use-pid-file = yes
; system-instance = no
; local-server-type = user
; enable-shm = yes
; shm-size-bytes = 0 # setting this 0 will use the system-default, usually 64 MiB
; lock-memory = no
; cpu-limit = no

; high-priority = yes
; nice-level = -11

; realtime-scheduling = yes
; realtime-priority = 5

; exit-idle-time = 20
; scache-idle-time = 20

; dl-search-path = (depends on architecture)

; load-default-script-file = yes
; default-script-file = /etc/pulse/default.pa

; log-target = auto
; log-level = notice
; log-meta = no
; log-time = no
; log-backtrace = 0

resample-method = speex-float-1
; enable-remixing = yes
; enable-lfe-remixing = no

flat-volumes = no

; rlimit-fsize = -1
; rlimit-data = -1
; rlimit-stack = -1
; rlimit-core = -1
; rlimit-as = -1
; rlimit-rss = -1
; rlimit-nproc = -1
; rlimit-nofile = 256
; rlimit-memlock = -1
; rlimit-locks = -1
; rlimit-sigpending = -1
; rlimit-msgqueue = -1
; rlimit-nice = 31
; rlimit-rtprio = 9
; rlimit-rttime = 1000000

; default-sample-format = s16le
; default-sample-rate = 44100
; default-sample-channels = 6
; default-channel-map = front-left,front-right,rear-left,rear-right,front-center,lfe

default-fragments = 8
default-fragment-size-msec = 10

; enable-deferred-volume = yes
deferred-volume-safety-margin-usec = 1
; deferred-volume-extra-delay-usec = 0[/B]

You must know, the values of default-sample-channels and default-channel-map was modified by me, but in the default configuration the problem was the same
I try changing the values of enable-remixing but nothing happens
Thanks for help

PD: Excuse me by my english, i am from Argentina and i don't speak english so well

---

### Post by CatKiller on 2013-04-05
Default-channel-map is probably the way to go, although I don't know that much about it, but that line in your configuration file is still commented out, so it won't have any effect.

A stereo sound source won't magically become surround sound, though. It's just going to mirror the front outputs to the rear ones. Might still be what you want, though, so that you don't have the sound stage leaping around as you change sources.

---

### Post by ddz0703 on 2013-04-05
Yes i know, a stereo audio file will sound like stereo for ever, but before a system update ubuntu cloned the adio stream to the rest of 5.1 channels.

But thanks for the data, i can solved the problem by my self
Always thought to comment a line in a .conf file y must to use the # character and not the ;

I uncomment and set the lines
[B]
 enable-remixing = yes
 enable-lfe-remixing = yes

 default-sample-channels = 6
 default-channel-map = front-left,front-right,rear-left,rear-right,front-center,lfe[/B]

Now pulseaudio don't reset my configuration. The problem is solved

---

