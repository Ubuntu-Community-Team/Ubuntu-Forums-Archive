---
title: "Alienware Area 51 m15x no audio through speakers - Ubuntu 13.10"
date: 2014-01-12
forum: General Help
---

### Post by ganeshmaharaj2 on 2014-01-12
Hi,
I just installed Ubuntu 13.10 on my Alienware m15x laptop but having issues trying to get audio working with speakers. I have audio over the headphone jack and i have tried all combinations that i could find on a google search. Choosing Speaker with headphones plugged in routes the audio over headphones but there was no way to get the audio via speakers with or without headphones connected.

have installed pauvcontrol and tried all options for /etc/modprobe.d/alsa-base.conf

This is my current configuration
alias snd-card-0 snd-hda-intel
alias sound-slot-0 snd-hda-intel
#alias sound-slot-1 snd-hda-intel


#options snd-hda-intel model=intel-alc889a enable_msi=1
#options snd-hda-intel model=laptop-eapd
options snd-hda-intel model=mb5

This is the output from alsa-info.sh
[http://www.alsa-project.org/db/?f=93d95a700c585e5b3b49e7e2c07464a1cc51d900](http://www.alsa-project.org/db/?f=93d95a700c585e5b3b49e7e2c07464a1cc51d900)

Please help me solve this. Apologies if this thread is a duplicate but nothing that i tried until now helped. :(

---

### Post by Drachyr on 2014-02-28
Hello, new to the forum/linux, but i too am having this issue. 
Excited to be joining the linux community though. Hated windows for long enough, and finally plucked up the courage to branch out.

---

