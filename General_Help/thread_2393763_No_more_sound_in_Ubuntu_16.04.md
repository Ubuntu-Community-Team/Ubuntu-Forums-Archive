---
title: "No more sound in Ubuntu 16.04"
date: 2018-06-07
forum: General Help
---

### Post by jj.wauters on 2018-06-07
Recently sound was stopping after some regular update on Ubuntu 16.04.
Sound is still working in Windows but no more for any user in Ubuntu.

I tried next :
[B]
Diagnosis
[/B]> $ lspci | grep Audio
00:03.0 Audio device: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor HD Audio Controller (rev 06)
00:1b.0 Audio device: Intel Corporation 8 Series/C220 Series Chipset High Definition Audio Controller (rev 04)

$ pacmd list-cards
0 card(s) available.

$ aplay -l
aplay: device_list:268: no soundcards found...



[B]Attempts to recover:
[/B]> 
$ pulseaudio -k && sudo alsa force-reload
Unloading ALSA sound driver modules: (none loaded).
Loading ALSA sound driver modules: (none to reload).

installed next Alsa package : 
[https://code.launchpad.net/~ubuntu-audio-dev/+archive/ubuntu/alsa-daily/+files/oem-audio-hda-daily-lts-xenial-dkms_0.201806010320~ubuntu16.04.1_all.deb](https://code.launchpad.net/~ubuntu-audio-dev/+archive/ubuntu/alsa-daily/+files/oem-audio-hda-daily-lts-xenial-dkms_0.201806010320~ubuntu16.04.1_all.deb)

added next to end of file /etc/modules :
snd-hda-intel



It seems there is no problem with pulseaudio, but Alsa is not working properly.

Can anyone help me to solve this issue?

Thanks

---

### Post by jj.wauters on 2018-06-14
Problem is solved.

I found next lines in /etc/modprobe.d/blacklist.conf
> 
#Blacklist microphone
blacklist snd_hda_intel

Sound is up again after removing these blacklist lines and running 
> ~$ sudo modprobe snd-hda-intel

---

