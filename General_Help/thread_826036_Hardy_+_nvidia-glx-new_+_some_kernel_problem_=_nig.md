---
title: "Hardy + nvidia-glx-new + some kernel problem = nightmare"
date: 2008-06-11
forum: General Help
---

### Post by yuv656 on 2008-06-11
I have spent my entire day trying to fix this problem. By now I'm so sick and tired I just feel like using Windows again (yes, I'm THAT sick and tired - and I don't feel like formatting and installing ubuntu all over again at this stage). I have also spent about 4 hours trying to squeeze advice from the normally helpful ubuntu community to no avail (IRC, this forum, launchpad).

I installed the nvidia-glx-new driver, and my sound stopped working. Ubuntu says I have no sound card installed. This is a known problem and can be found here and there on google. It's something related to the kernel, and some depency - it's above my level of linux expertise. I tried a variety of suggested fixes to no avail.

I came upon this thread:
[https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.24/+bug/188287/](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.24/+bug/188287/)
Where pdragon says how he solved it in the comments. I tried his advice, and now Ubuntu does recognize my sound card, but it insists on playing all sound through my *pc speaker*. Double clicking on the volume manager and then on Change Device shows only 3 different pc speaker related options.

---

### Post by nikgare on 2008-06-11
Have you tried changing the default sound output here:

System->Preferences->Multimedia Systems Selector

Nik

---

### Post by yuv656 on 2008-06-11
Thanks for the reply. 

I don't have a Multimedia Systems Selector option under Preferences

---

### Post by nikgare on 2008-06-12
Then run:

gstreamer-properties


Nik

---

### Post by yuv656 on 2008-06-12
Under Default Output, ALSA is selected at Plugin, and under Device the only options are "Default" and "pc speaker".

If I change the Default Output to anything other than ALSA, the Device option becomes grayed out with the text "Unsupported", and if I play a test sound, it still comes through the pc speaker :/

---

### Post by nikgare on 2008-06-15
My plugin is set to Autodetect, but my Device says unsupported.
When I try the test sound, the sound comes through the right speakers, not the PC onboard speaker.
This seems to be the same if I select pulse audio instead - both ALSA and OSS throu uip error when I try to play a sound.
What sound card do you have (lspci)?

Nik

---

### Post by yuv656 on 2008-06-16
I have tried different combinations of settings but all of them still cause sound to be played through the pc speaker.

```
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)
	Subsystem: Intel Corporation Unknown device 3001
	Flags: fast devsel, IRQ 23
	Memory at e3220000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>

```

---

### Post by nikgare on 2008-06-16
I don't really know what else to suggest, but I have found something similar here:
[http://ubuntuforums.org/showthread.php?t=661102](http://ubuntuforums.org/showthread.php?t=661102)
Maybe this will help,
Nik

---

### Post by Erlander on 2008-06-17
On boot up press Esc and select a different kernel.

I found my onboard sound was not recognised because I had installed some other kernels trying to get the nvidia new drivers working on my second Ubuntu pc.

The sound drivers are normally in the kernel except some versions don't include them.

So try a few different ones that are in your GRUB menu and see if they help.

good luck.

Rob

---

