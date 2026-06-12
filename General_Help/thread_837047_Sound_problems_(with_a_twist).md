---
title: "Sound problems (with a twist)"
date: 2008-06-22
forum: General Help
---

### Post by clemmyboy on 2008-06-22
Hi,

I'm a newbie to Linux but have a lot of experience in Windows. I have read countless threads and discussions about problems with sound on Ubuntu and the outcome is usually it works or it doesn't. My problem is it works for some applications such as Amorok and Rhythmbox but not others such as Firefox or general system sounds.

I am using 64bit Ubuntu Hardy Heron 8.04. I have an old Creative Soundblaster Value card and using USB speakers.

When I unplug my speakers and put them back in I hear a sound which sounds like a system start up sound. However, I cannot get general system sounds. I can hear the tone when I go to System>Preferences>Sound and click the Test sound buttons. But, I can't hear the sounds when I go to the "sounds" tab and click the "play" buttons.

As a newbie I really like Ubuntu but this problem with sound is a bit off-putting. Believe me, I spent hours trawling though other threads about this problem and the solutions seems to work for some but not others. My problem is my card is recognised, my speakers work, but only for certain applications.

Can anyone with similar problems help me out? If you need more info about my setup, please let me know.

Cheers
Clem

---

### Post by knutschr on 2008-06-22
I don't know if this solve your problem, but I have had very good experience with this tutorial by reassuringlyoffensive;
[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

---

### Post by doug1212 on 2008-06-22
Hi,
You appear to have two separate sound systems, the Creative card and the USB speakers.

I think it may be a case of selecting the default sound device in preferences > sound.

Doug.

---

### Post by doug1212 on 2008-06-22
Found this thread on forcing alsa to use a certain snd card as the default.
Hope it helps.
Doug.

[HTML]http://ubuntuforums.org/archive/index.php/t-618199.html[/HTML]

---

### Post by hefeloce on 2008-06-22
Well I don't know about two sound systems... But about firefox, maybe is the flash issue, it is solved by installing the libflash-mozplugin from synaptic or from apt

from apt write on a terminal:
apt-get install libflash-mozplugin
as root (that means with sudo)

---

### Post by clemmyboy on 2008-06-27
Thank you all very much for the info and the really comprehensive links. However... I'm afraid there is still no system sound or sound with flash after following the guides.

One thing I noticed though. When I go to system>sound>properties I am able to select my sound device as ALSA - Advanced Linux Sound Architecture rather than USB Device and this seems to work with the "test" buttons and it didn't before.

Also Amorok works ok to play MP3 and streaming radio.

Does this shed any light?

Cheers
Clem

---

### Post by clemmyboy on 2008-06-28
I've dug a hole I can't get out of...

I've been using terminal to play around with default devices and now I have lost all the ones I saw previously e.g Alsa Mixer USB, LIVE, and around 5 others to do with sound capture.

When I go to Sytem>Preferences>Sound the Device shows SigmaTel STAC9721,23 (OSS Mixer) and there are no other options from the drop-down menu (when there used to be before). When my sound (through music players) worked, ALSA was selected and now it's gone. It seems SigmaTel is my only option and this does not work at all.

Please help me get the others back - it might save my marriage as I will be able to spend more time with my wife rather than trying to fix a sound problem.

Thanks
Clem

---

### Post by clemmyboy on 2008-07-04
Happy days!

I fixed the problem by installing PulseAudio Applet and changing my "Default Mixer Tracks" in System>>Preferences>>Sound to Playback: ALSA PCM on front:1 (USB Audio) via DMA (PulseAudio Mixer).

By the way in PulseAudio mixer, I had to click on volume control>output devices tab and right click on the device (the USB one) I wanted to use and tick the default tab that pops up. 

As a Linux newbie I really appreciate the suggestions everyone has contributed and I really hope my post will help someone else out.

Cheers!
Clem

---

