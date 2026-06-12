---
title: "TIP: Problem With a socket directory from PulseAudio"
date: 2008-04-08
forum: General Help
---

### Post by SneakyWho_am_i on 2008-04-08
pulseaudio is a powerful and strange beast.

Today I restarted X... Actually I think I restarted the whole machine. Later when I tried to start pulseaudio, I couldn't.
There are some crazy people out there who will tell you that pulseaudio is a drop-in replacement for esd, and that it will start every time an application requests sound or somesuch.
This never happened for me under Edubuntu Gutsy or Xubuntu Hardy, so basically I don't believe it.

Anyway, starting pulseaudio thus:
```
pulseaudio
```
.....

Did nothing.

I found the thing to be not running:
```
ps aux|grep pulse
```
The output only had one line, a process called "grep"... No joy.

So instead of using ALT+F2, I tried to use Konsole as a kind of debugger:
```
sneaky@ubuntu:~$ pulseaudio
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL front:0
W: alsa-util.c: Device front:0 doesn't support 44100 Hz, changed to 48000 Hz.
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL front:0
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL front:1
E: module-protocol-stub.c: Failed to create socket directory '/tmp/.esd-1000/socket': Not a directory
E: module.c: Failed to load  module "module-esound-protocol-unix" (argument: ""): initialization failed.
E: main.c: Module load failed.
E: main.c: Failed to initialize daemon.
```

Google seemed really helpful but nobody offered a solution to my exact problem (that I saw)

```
ls -la /tmp
``` showed something like this:

```
sneaky@ubuntu:~$ ls -la /tmp
total 56
drwxrwxrwt 12 root   root   4096 2008-04-09 08:25 .
drwxr-xr-x 21 root   root   4096 2008-04-05 11:36 ..
drwx------  2 sneaky sneaky 4096 2008-04-09 08:24 .esd-1000
drwx------  3 sneaky sneaky 4096 2008-04-09 08:24 gconfd-sneaky
drwxrwxrwt  2 root   root   4096 2008-04-09 02:05 .ICE-unix
drwx------  2 sneaky sneaky 4096 2008-04-09 08:31 ksocket-sneaky
drwx------  2 sneaky sneaky 4096 2008-04-09 08:24 orbit-sneaky
drwx------  2 sneaky sneaky 4096 2008-04-09 08:24 pulse-sneaky
drwxr-xr-x  2 root   root   4096 2008-04-09 02:05 .winbindd
drwx------  3 sneaky sneaky 4096 2008-04-09 02:06 .wine-1000
-r--r--r--  1 root   root     11 2008-04-09 02:05 .X0-lock
drwxrwxrwt  2 root   root   4096 2008-04-09 02:05 .X11-unix
-rw-------  1 sneaky sneaky  203 2008-04-09 02:05 .xfsm-ICE-ITA38T
```

That was not very good.

.esd-1000 was a broken symlink to .esd in the same directory.
Your mileage may vary but this seemed to fix it for me:
```
#clear out your /tmp/ directory. I will not tell you how to do this as it could be used for evil
mkdir /tmp/.esd
```

It might help to make that .esd directory 777 - frankly i don't know what permissions it should have. I admit I don't know a great deal about this sort of thing yet

```
sneaky@ubuntu:~$ ls -la /tmp
total 56
drwxrwxrwt 12 root   root   4096 2008-04-09 08:25 .
drwxr-xr-x 21 root   root   4096 2008-04-05 11:36 ..
drwx------  3 sneaky sneaky 4096 2008-04-09 08:14 .esd
drwx------  2 sneaky sneaky 4096 2008-04-09 08:24 .esd-1000
drwx------  3 sneaky sneaky 4096 2008-04-09 08:24 gconfd-sneaky
drwxrwxrwt  2 root   root   4096 2008-04-09 02:05 .ICE-unix
drwx------  2 sneaky sneaky 4096 2008-04-09 08:31 ksocket-sneaky
drwx------  2 sneaky sneaky 4096 2008-04-09 08:24 orbit-sneaky
drwx------  2 sneaky sneaky 4096 2008-04-09 08:24 pulse-sneaky
drwxr-xr-x  2 root   root   4096 2008-04-09 02:05 .winbindd
drwx------  3 sneaky sneaky 4096 2008-04-09 02:06 .wine-1000
-r--r--r--  1 root   root     11 2008-04-09 02:05 .X0-lock
drwxrwxrwt  2 root   root   4096 2008-04-09 02:05 .X11-unix
-rw-------  1 sneaky sneaky  203 2008-04-09 02:05 .xfsm-ICE-ITA38T
```

my .esd-1000 had turned from red to blue. This is a good sign. pulseaudio ran OK now too.
I say that .esd might need to be 777 or something because otherwise how will other users use pulse??
What I've done worked fine for me.
In any event i hope that this post helps anyone with the same error message who doesn't have any brilliant troubleshooting ideas.
I was quite proud of myself for finding it but I'm open to any and all suggestions from more experienced users about this.

---

