---
title: "No sound through headphones ubuntu 17.04"
date: 2017-10-27
forum: General Help
---

### Post by yashboura on 2017-10-27
I have actually two headphones port in my CPU , both works fine (I checked with Windows 10 ). One port which is on front doesn't work for me. Also every thing is unmuted in alsamixer.

My alsamixer info is [http://www.alsa-project.org/db/?f=0a33e46c8033ad43db5976577d638f6c440570d2](http://www.alsa-project.org/db/?f=0a33e46c8033ad43db5976577d638f6c440570d2)

Please help .

---

### Post by ajgreeny on 2017-10-27
Are the headphone ports also unmuted and set to a high enough volume in **pulseaudio-volume-control**, ie Sound-Settings from the volume panel-icon?

---

### Post by Yellow Pasque on 2017-10-27
Have you tried disabling 'Independent HP' in alsamixer?

---

### Post by yashboura on 2017-10-28
yes the headphone ports are unmuted and also the sound is maximum!

---

### Post by yashboura on 2017-10-28
> **Temüjin said:**
> Have you tried disabling 'Independent HP' in alsamixer?
THanks!!!! IT worked but the problem is the headphone port keep getting back to umute option after every reboot ( AUTO MUTE IS DISABLED TOO!) . Any solution for this?

---

