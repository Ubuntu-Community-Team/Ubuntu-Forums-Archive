---
title: "No sound at all"
date: 2014-09-15
forum: General Help
---

### Post by christoph5 on 2014-09-15
reported bug that my sound doesent work at all, look please, tell me what to do??a
[https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/824097](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/824097)

---

### Post by christoph5 on 2014-09-15
IEC958 Playback AC97-SPSA showed in a output in terminal, then i googled it and i found this
[http://www.mechanicalcat.net/richard/log/Noise/Why_Linux_isn_t_ready_for_the_masses__part_two_bazillion](http://www.mechanicalcat.net/richard/log/Noise/Why_Linux_isn_t_ready_for_the_masses__part_two_bazillion)

> So the sound stopped working in the HTPC yesterday. Usually I just go  through a relatively arcane interface to set the unfathomably-named  "IEC958 Playback AC97-SPSA" setting to "0". This does something. And it  usually makes the sound work.
 Last night it didn't. I spent 40 minutes fiddling with the alsamixer interface trying to make sound come out of the computer.
 In the end, I found a complete "asound.state" file online that I  compared against my "/var/lib/alsa/asound.state" file. The culprit? A  setting called "IEC958 Playback Default" which had the value:


> '008200000000000000000000000000000000000000000000000000000000000000000000
0000000000000000000000000000000000000000000000000000000000000000000000000
0000000000000000000000000000000000000000000000000000000000000000000000000
0000000000000000000000000000000000000000000000000000000000000000000000000
0000000000000000000000000000000000000000000000000000000000000'

how can i change it like this guy did?

---

### Post by christoph5 on 2014-09-17
please answear my question

---

