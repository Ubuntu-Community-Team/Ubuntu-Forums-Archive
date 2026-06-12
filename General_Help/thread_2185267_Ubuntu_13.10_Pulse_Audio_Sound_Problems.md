---
title: "Ubuntu 13.10 Pulse Audio Sound Problems"
date: 2013-11-01
forum: General Help
---

### Post by tecknomage on 2013-11-01
**REF:** Ubuntu 13.10 with GNOME Flashback desktop

Thanks to replies elsewhere I was given two sources to look at:
[PulseAudio Ubuntu Wiki]("https://wiki.ubuntu.com/PulseAudio") and [Padsp Linux Main Page]("http://linux.die.net/man/1/padsp").

Sadly neither had info that solved my sound problem :icon_frown:

Several games have warbling or cycling sound. **The sound IS there, it is NOT choppy, but sounds like it's cycling or repeating.**

Two games use the "padsp" _PulseAudio Wrapper_ prefix. Even tried it with two of the switches listed in the *Padsp Linux Main Page*, no help.

Via another post on using Terminal commands I found the following info:

**Audio Adapter (hardware)**
HDA-Intel - HDA Intel
Driver = snd_hda_intel

**Codec:**
Realteck ALC662
Motorola Si3054

On the Codec, anyone see something wrong with having two running :confused:

**How do I change the Codec being used by Ubuntu 13.10?**

---

### Post by vbgunz on 2014-01-08
I'm not sure how far you've gone into messing with settings but I've gone through the same issue and managed on my own to find a simple fix. Hopefully this will work out for you.

Escalate your privileges and edit the following file (make sure to back up the file first).

```
/etc/pulse/daemon.conf
```

Change the following directives to reflect the following (remove the prefixed semi-colon, otherwise it'll never get read).

```

daemonize = yes
cpu-limit = yes 
nice-level = 0
```

Reboot, hopefully the garbled noises and other issues get fixed in the process.

Good luck!

---

### Post by R33D3M33R on 2014-01-25
I have been having similar audio problems for a very long time. Setting tsched=0 in /etc/default/default.pa fixed problems in some programs, but broke others. However, the solution above seems to fix problems in both. Thanks, vbgunz!

/edit: It actually didn't work. After reboot, sound is skipping again.

---

