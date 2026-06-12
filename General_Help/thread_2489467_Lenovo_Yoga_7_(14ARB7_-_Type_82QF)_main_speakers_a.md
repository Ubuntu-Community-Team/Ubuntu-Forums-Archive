---
title: "Lenovo Yoga 7 (14ARB7 - Type 82QF) main speakers and microphone not working"
date: 2023-07-31
forum: General Help
---

### Post by lakimens2 on 2023-07-31
Hi,

I recently installed Ubuntu as I don't like using Windwos and I managed to resolve most of my issues (mostly regarding touch controls and gestures), however, I have not been able to resolve this.

The speakers sound awful, as far as I see on the internet, it's because only two of the 4 speakers are working. Furthermore, the microphone is not working.

All the fixes on the net are similar to what is mentioned in this thread: [https://forums.lenovo.com/t5/Ubuntu/Yoga-7i-sound-card-issue-on-Linux/m-p/5183746](https://forums.lenovo.com/t5/Ubuntu/Yoga-7i-sound-card-issue-on-Linux/m-p/5183746)

I tried entering the options in the /etc/modprobe.d/alsa-base.cnf file, however, it did not help.

Additionally, I also found suggestions to install the OEM kernel (6.1.0-1017-oem is the one I have) and this did not help as well.

Do you have any other suggestions as to how I might resolve the issue? Thanks!

---

### Post by lakimens2 on 2023-08-19
Anyone?

---

### Post by lakimens2 on 2023-08-19
Probably should've posted this as well:

inxi -A
Audio:
  Device-1: AMD driver: snd_hda_intel
  Device-2: AMD Raven/Raven2/FireFlight/Renoir Audio Processor
    driver: snd_pci_acp6x
  Device-3: AMD Family 17h HD Audio driver: snd_hda_intel
  Sound Server-1: ALSA v: k6.2.0-26-generic running: yes
  Sound Server-2: PulseAudio v: 15.99.1 running: yes
  Sound Server-3: PipeWire v: 0.3.48 running: yes

---

