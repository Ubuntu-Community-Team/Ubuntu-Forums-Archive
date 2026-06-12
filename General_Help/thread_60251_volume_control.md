---
title: "volume control"
date: 2005-08-27
forum: General Help
---

### Post by Nopposan on 2005-08-27
Well I just installed the proper kernel (was running 686 with AMD, now running k7).  'Thought I'd try out the DVD player to see if it works better with the new kernel; it seems to stall much less often and for shorter winks.  However, THERE'S NO SOUND!

I tried all of the various methods I could find for controling the volume in Totem and from the Gnome volume control software.  Please offer me other options to test out.

---

### Post by Nopposan on 2005-09-04
O.K., here are some more details for the 20+ people who have viewed my post but didn't have a response; 'guess I was stingy with my description of the problem.

I supposedly reinstalled the alsamixergui, but I still don't see it under the Applications or System menus.  When I menu over to the Preferences-->Multimedia Systems Selector and use this program to check on things I get the following errors when testing the output:

Error#1:Failed to construct test pipeline for 'ALSA - Advanced Linux Sound Architecture'
Error#2:Failed to construct test pipeline for 'Artsd - ART Sound Daemon'
Error#3:Failed to construct test pipeline for 'OSS - Open Sound System'

The ESD output is fine.

I get the following errors when testing the input:
Error #1:Failed to construct test pipeline for 'ALSA - Advanced Linux Sound Architecture'
Error#2:Failed to construct test pipeline for 'ESD - Enlightenment Sound Daemon'
Error#3:Failed to construct test pipeline for 'OSS - Open Sound System'
Error#4:Failed to construct test pipeline for 'Silence'
Error#5:Failed to construct test pipeline for 'Custom'

At least Phillip Glass' masterpiece is being given equal treatment.


Here's a whole bunch of information I don't understand; if any of you do, then lend a boy a hand, willya?

nopposan:~$ lsmod|grep snd
snd_via82xx            27616  2
snd_ac97_codec         74208  1 snd_via82xx
snd_pcm_oss            52516  1
snd_mixer_oss          19776  2 snd_pcm_oss
snd_pcm                94920  3 snd_via82xx,snd_ac97_codec,snd_pcm_oss
snd_timer              25156  1 snd_pcm
snd_page_alloc          9796  2 snd_via82xx,snd_pcm
gameport                4544  1 snd_via82xx
snd_mpu401_uart         7744  1 snd_via82xx
snd_rawmidi            24928  1 snd_mpu401_uart
snd_seq_device          8524  1 snd_rawmidi
snd                    55268  9 snd_via82xx,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer,snd_mpu401_uart,snd_rawmidi,snd_seq_device
soundcore              10080  3 snd

---

