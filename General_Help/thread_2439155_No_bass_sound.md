---
title: "No bass sound"
date: 2020-03-23
forum: General Help
---

### Post by ignissak on 2020-03-23
I am using Ubuntu 18.04.3 LTS on Xiaomi Mi Notebook Pro.
I cannot hear any bass coming from built-in speakers but I can from plugged headphones.

```
[COLOR=#242729][FONT=Consolas]jacob@jacobbrds:~$ pacmd list-sinks | grep sample
[/FONT][/COLOR][COLOR=#242729][FONT=Consolas]sample spec: s32le 2ch 44100Hz[/FONT][/COLOR]
```

My /etc/pulse/deamon.conf:
```
[COLOR=#242729][FONT=Consolas]daemonize = no[/FONT][/COLOR]; fail = yes
; allow-module-loading = yes
; allow-exit = yes
; use-pid-file = yes
; system-instance = no
; local-server-type = user
; enable-shm = yes
; enable-memfd = yes
; shm-size-bytes = 0 # setting this 0 will use the system-default, usually 64 MiB
; lock-memory = no
; cpu-limit = no

high-priority = yes
nice-level = -11

realtime-scheduling = yes
realtime-priority = 9

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

resample-method = src-sinc-medium-quality
; avoid-resampling = false
; enable-remixing = yes
; remixing-use-all-sink-channels = yes
enable-lfe-remixing = no
; lfe-crossover-freq = 0

flat-volumes = no

rlimit-fsize = -1
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
rlimit-rtprio = 9
; rlimit-rttime = 200000

default-sample-format = s24le
default-sample-rate = 96000
alternate-sample-rate = 44100
default-sample-channels = 2
default-channel-map = front-left,front-right

default-fragments = 2
default-fragment-size-msec = 125

; enable-deferred-volume = yes
deferred-volume-safety-margin-usec = 1 [COLOR=#242729][FONT=Consolas]; deferred-volume-extra-delay-usec = 0[/FONT][/COLOR]
```
lscpi -v ouput: [https://hastebin.com/horovuzuse.rb](https://hastebin.com/horovuzuse.rb)

---

