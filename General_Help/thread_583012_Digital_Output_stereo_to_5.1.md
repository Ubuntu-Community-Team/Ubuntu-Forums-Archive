---
title: "Digital Output stereo to 5.1"
date: 2007-10-20
forum: General Help
---

### Post by athanasfire on 2007-10-20
I'm new to linux and have just installed Gutsy. I'm slowly learning the ropes but despite all my efforts i've had no luck with getting the sound how I want.

In windows I can output stereo sound from my media player into a dolby encoder and then that will give me - false - 5.1 surround to my digital speakers.

I have tried a number of things including playing with alsamixer and unmuting the switches in the sound control pannel including surround side, lfe and centre. 

There was a post on the Alsa wiki [http://alsa.opensrc.org/index.php/Playing_stereo_on_surround_sound_setup_%28Howto%29](http://alsa.opensrc.org/index.php/Playing_stereo_on_surround_sound_setup_%28Howto%29)
which i tried but no luck.

My sound device is an onboard CMI9880 chip

info:
tony@Antony:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: CMI9880 [CMI9880]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: CMI9880 Digital [CMI9880 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

also
when i do 
tony@Antony:~$ speaker-test -D surround51 -c 6
i don't get pink noise from speakers except the front left and right

Any help would be much appreciated.

btw. The sound works fine now but only in stero PCM 2/0 48

---

