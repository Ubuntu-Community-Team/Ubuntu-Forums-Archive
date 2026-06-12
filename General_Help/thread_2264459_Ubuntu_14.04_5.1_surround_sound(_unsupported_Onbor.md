---
title: "Ubuntu 14.04 5.1 surround sound?( unsupported Onbored Sound Card)"
date: 2015-02-07
forum: General Help
---

### Post by RageMachine on 2015-02-07
Thanks everyone who tryed to help, i have done lots of googling, Only to find out that my Onbored sound card is not fully suported as of yet. its the Onbored soundcard from a Gigabyte G1 Sniper M5 : Creative CA0132
From what i can tell everything on this card Crystal voice, Dialog Plus, EchoC, Eq,PlayEnha, Smart volume, all work just not the 5.1 / 7.1.

> Hello all, ive been around off and on for a few years now with linux, testing out the waters every so offten. I would have to say im a little more than hip deep now.
Memory express was having sails on ssd's so i picked one up and installed Ubuntu 14.04. i find my self using Ubunutu more than windows 8 now!

i would have switch to linux long ago but i love games and windows is where the games are? wait steam on linux! just under half my game library works on ubuntu!
and with Nivdia and AMD showing more love with their driver's

witch brings me to my problem Sound! i have built in 5.1 on my MOBO and it dusnt work sound comes from the F left and F right but nothing else did some googling and found this link[https://help.ubuntu.com/community/SurroundSound](https://help.ubuntu.com/community/SurroundSound) among others but still no luck getting the other channels to work.
oh im using the default ubutnu sound pulsaudio, and now that i change that file my sound is out of sync.

[QUOTE]; daemonize = no
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

resample-method = speex-float-3
 enable-remixing = yes
 enable-lfe-remixing = yes

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
; alternate-sample-rate = 48000
; default-sample-channels = 6
; default-channel-map = front-left,front-right,rear-left,rear-right,front-center,lfe

default-fragments = 8
default-fragment-size-msec = 10

; enable-deferred-volume = yes
deferred-volume-safety-margin-usec = 1
; deferred-volume-extra-delay-usec = 0

thanks if ya can helps me out, and sorry if this was posted in the wrong sport. if ya need more info just ask.[/QUOTE]

---

### Post by RageMachine on 2015-02-08
im running ubuntu 14.04, the MOBO is a g1.sniper m5, CPU i7 4770k

---

### Post by Yellow Pasque on 2015-02-08
> oh im using the default ubutnu sound pulsaudio, and now that i change that file my sound is out of sync.

So what exactly did you change and did you try changing it back?

---

### Post by RageMachine on 2015-02-08
yep sorry i forgot to post that, After i restored the settings in the file it put the audio back in sync.

---

### Post by Yellow Pasque on 2015-02-08
Have you selected 5.1 Surround Sound in the audio settings? I don't know too much about Unity Desktop, but regardless of what environment you're using, you can always use pavucontrol:
```
sudo apt-get install pavucontrol
pavucontrol
```

---

### Post by RageMachine on 2015-02-11
i installed pavucontrol as suggested and now my hdmi 5.1 shows up thx for the help guys, did some more googling and found out that the onbored sound card is not fully supported in linux as of yet. and as its from creative it will most likly be a long time befor it ever gets their guess im going to have to get a new sound card.
any ideas on a nice not overpriced card?

since i have installed Ubuntu 14.04 i havent tuched windows 8, i think i just might have switch!!!
ill check this out tomorrow and edit it it to show unsupported card and put up the sound card info its late right now im headding to bed.

---

