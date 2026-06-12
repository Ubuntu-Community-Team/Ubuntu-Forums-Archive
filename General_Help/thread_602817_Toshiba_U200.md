---
title: "Toshiba U200"
date: 2007-11-04
forum: General Help
---

### Post by muadib on 2007-11-04
I am having trouble getting the mic working on my Toshiba U200, it is running:

[mathieu2@durnik]~$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 7.04
Release:        7.04

And Ubuntu Linux Kernel:
[mathieu2@durnik]~$ uname -r
2.6.20-16-386

The sound output works, I can play mp3s videos no problem but I am unable to use the mic, I have tested different alsa settings with no luck using alsamixer.

I can confirm that the mic that I tested the card with works as I just tested it on another laptop and it worked nicely.

Current loaded modules include:

[mathieu2@durnik]~$ lsmod|grep snd
snd_hda_intel          20504  5 
snd_hda_codec         204160  1 snd_hda_intel
snd_pcm_oss            43264  1 
snd_mixer_oss          16512  1 snd_pcm_oss
snd_pcm                76680  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           3844  0 
snd_seq_oss            31616  0 
snd_seq_midi            8576  0 
snd_rawmidi            24448  1 snd_seq_midi
snd_seq_midi_event      7424  2 snd_seq_oss,snd_seq_midi
snd_seq                49648  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              22276  2 snd_pcm,snd_seq
snd_seq_device          8204  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    51716  18 snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               7520  2 snd
snd_page_alloc          9992  2 snd_hda_intel,snd_pcm

And lspci gives the following reference to audio:

[mathieu2@durnik]~$ lspci|grep Audio
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)

Any help would be appreciated.

---

### Post by mamep on 2007-12-05
Did u fix it?

---

### Post by muadib on 2007-12-12
No I have not found a fix for this yet.

---

### Post by mamep on 2007-12-14
I saw a small patch at alsa-projects bug repository but it does not seems to fix the problem..

---

