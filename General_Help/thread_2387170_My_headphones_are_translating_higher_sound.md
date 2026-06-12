---
title: "My headphones are translating higher sound"
date: 2018-03-15
forum: General Help
---

### Post by velemarvlasov on 2018-03-15
Hello! I'm a newfag in Ubuntu, and have a big problem with my headphones (Jabra Evolve 65) - they are translating sound with higher notes, if I connect my headphones with usb-cable, and losing some freaquency with bluetoth (sounds rly bad). If I using my Jabra with other devices - works good, usual headphones with 3.5 - sounds good, using integrated dynamics of my laptop - good too. Only with my Jabra I everythime hear higher voices and music :( Who can help me with fix this bug?
Ubuntu 16.04, Lenovo t460s, Jabra Evolve 65. I can get any extra info.

---

### Post by #&amp;thj^% on 2018-03-15
> **velemarvlasov said:**
> Hello! I'm a newfag in Ubuntu, and have a big problem with my headphones (Jabra Evolve 65) - they are translating sound with higher notes, if I connect my headphones with usb-cable, and losing some freaquency with bluetoth (sounds rly bad). If I using my Jabra with other devices - works good, usual headphones with 3.5 - sounds good, using integrated dynamics of my laptop - good too. Only with my Jabra I everythime hear higher voices and music :( Who can help me with fix this bug?
Ubuntu 16.04, Lenovo t460s, Jabra Evolve 65. I can get any extra info.

You know I remember this not so long ago with someone else and lets see if this will help here also.
You will need to edit this file as root via:

```
sudo nano /etc/pulse/daemon.conf
```
And edit the line "**; default-sample-rate = 44100**"
to:
```
default-sample-rate = 48000
```
Save with <ctrl+x> and yes save.
Now kill pulse audio and restart via:
```
pulseaudio -k
```
Now any improvement?

---

### Post by velemarvlasov on 2018-03-16
No, it's not :( It still higher. Have you any idea?

---

### Post by #&amp;thj^% on 2018-03-16
> **velemarvlasov said:**
> No, it's not :( It still higher. Have you any idea?

Let's have a look at:
```
gedit /etc/pulse/daemon.conf
```

---

### Post by velemarvlasov on 2018-03-16
One min

---

### Post by velemarvlasov on 2018-03-16
# This file is part of PulseAudio.
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
# along with PulseAudio; if not, see <http://www.gnu.org/licenses/>.


## Configuration file for the PulseAudio daemon. See pulse-daemon.conf(5) for
## more information. Default values are commented out.  Use either ; or # for
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


; resample-method = speex-float-1
; enable-remixing = yes
; enable-lfe-remixing = yes
; lfe-crossover-freq = 120


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
; rlimit-rttime = 200000


; default-sample-format = s16le
; default-sample-rate = 48000
; alternate-sample-rate = 48000
; default-sample-channels = 2
; default-channel-map = front-left,front-right


; default-fragments = 4
; default-fragment-size-msec = 25


; enable-deferred-volume = yes
deferred-volume-safety-margin-usec = 1
; deferred-volume-extra-delay-usec = 0

Is that right?

---

### Post by #&amp;thj^% on 2018-03-16
Well you followed my instructions, but it was my fault here with this:
```
; default-sample-rate = 48000
```
Remove the leading "**;**"
with this again:
 ```
sudo nano /etc/pulse/daemon.conf
```
now it should look like this:
```
default-sample-rate = 48000
```
And restart pulseaudio:
```
pulseaudio -k
```
Now see if any improvement.

---

### Post by velemarvlasov on 2018-03-16
It's all fixed! Thank you so much.

---

### Post by #&amp;thj^% on 2018-03-16
Great! glad that is still working. :)
If satisfied with this workaround consider marking this as solved as to help others.

---

### Post by velemarvlasov on 2018-03-18
I'm sorry, it's problem are back again. What else should we do to resolve it?

---

### Post by #&amp;thj^% on 2018-03-18
> **velemarvlasov said:**
> I'm sorry, it's problem are back again. What else should we do to resolve it?

You may have had an update that changed this file, so lets look at this again:
```
gedit /etc/pulse/daemon.conf
```
The **real** problem here is that the firmware used by your headset from the manufacturer and alsa conflict leaving you with the chipmunk sounds.

---

### Post by velemarvlasov on 2018-03-19
```
# This file is part of PulseAudio.
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
# along with PulseAudio; if not, see <http://www.gnu.org/licenses/>.


## Configuration file for the PulseAudio daemon. See pulse-daemon.conf(5) for
## more information. Default values are commented out.  Use either ; or # for
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


; resample-method = speex-float-1
; enable-remixing = yes
; enable-lfe-remixing = yes
; lfe-crossover-freq = 120


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
; rlimit-rttime = 200000


; default-sample-format = s16le
default-sample-rate = 48000
; alternate-sample-rate = 48000
; default-sample-channels = 2
; default-channel-map = front-left,front-right


; default-fragments = 4
; default-fragment-size-msec = 25


; enable-deferred-volume = yes
deferred-volume-safety-margin-usec = 1
; deferred-volume-extra-delay-usec = 0
```

---

### Post by wildmanne39 on 2018-03-19
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by velemarvlasov on 2018-03-19
Ok, I will

---

### Post by #&amp;thj^% on 2018-03-19
> **wildmanne39 said:**
> Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.
+1 Thanks wildmanne39 ;)

> **velemarvlasov said:**
> I'm sorry, it's problem are back again. What else should we do to resolve it?
This is what I'm trying to explain here, Obviously this should not happen if all layers are aware of the recording sample rate and adjust playback accordingly.
Please be aware that this is just a workaround and not a permanent fix:
Bug was Reported I see now here: [https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/1710060](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/1710060)

And as I don't have your headset here on my end to test you are my only way of testing various settings, so please keep records here as to the steps taken. (So if needed to change back)
I only want to make very small sensible changes here.
Now lets un-comment the line above "default-sample-rate = 48000"
This Line: **(; default-sample-format = s16le)**
To now read like:
```
default-sample-format = s16le
```
Using the same method we did before:
```
sudo nano /etc/pulse/daemon.conf
```
Save and Reload pulseaudio:
```
pulseaudio -k
```

---

### Post by velemarvlasov on 2018-03-19
It's done, still dosen't help :( And point: The daemon could not be terminated: There is no such process (was translated from russian). Have you any idea?

---

### Post by #&amp;thj^% on 2018-03-19
> **velemarvlasov said:**
> It's done, still dosen't help :( And point: The daemon could not be terminated: There is no such process (was translated from russian). Have you any idea?

pulseaudio is very ginger on xenail try again, or log out and back in again.

---

### Post by velemarvlasov on 2018-03-19
I dont know why are this isn't running. How can I launch it? I have log outed and back it again - no results.

---

### Post by #&amp;thj^% on 2018-03-19
Ok then we get a bit tougher on pulse with:
```
rm -rf ~/.config/pulse 
```
now:
```
pulseaudio -k
```

---

### Post by velemarvlasov on 2018-03-19
It's nothing happens when:
[COLOR=#000000]Code:[/COLOR]
rm -rf ~/.config/pulse

---

### Post by #&amp;thj^% on 2018-03-19
yes it did, you would not see it in the terminal, please just follow the instructions.:)

---

### Post by velemarvlasov on 2018-03-19
[IMG]https://pp.userapi.com/c846218/v846218496/372d/Zijy3N78YHg.jpg[/IMG]

---

### Post by #&amp;thj^% on 2018-03-19
I see we have a translation problem communicating with each other. ;)
That window looks as expected>>>meaning it worked.
Now run 
```
pulseaudio -k
```

---

### Post by velemarvlasov on 2018-03-19
[IMG]https://pp.userapi.com/c847016/v847016496/3dc1/oPrHUwXdhts.jpg[/IMG]
Translation: The daemon could not be terminated: There is no such process

---

### Post by #&amp;thj^% on 2018-03-19
Now try then to play something through your headset.

---

### Post by velemarvlasov on 2018-03-19
It's still higher, nothing was fixed

---

### Post by #&amp;thj^% on 2018-03-19
As I said>>This is not a Fix. Workaround and Fix are totaly different.
```
sudo nano /etc/pulse/daemon.conf
```
Change back to 
```
; default-sample-format = s16le
```
And 
```
; default-sample-rate = 44100
```
My friend I have reached my end here to help.
Until the bug is fixed, and i doubt by the looks of things on the link i provided in post#15 that it won't be fixed in 16.04.
We gave a good effort here to try though.
Regards

---

