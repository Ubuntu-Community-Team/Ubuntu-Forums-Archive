---
title: "Flash Freezing"
date: 2007-06-03
forum: General Help
---

### Post by Mike_88 on 2007-06-03
Flash was working fine in Feisty up until I did a kernel upgrade the other day.  Since then I am having problems playing flash videos in both Opera and Firefox, on any site that uses flash to display video,  The videos tend to play fine for some time, but then after a while they start to freeze.  It will play for about 2-3 seconds and then pause.  If I fast forward the video it will start playing again, but will once again freeze after about 2-3 seconds.  I am using Flash 9 (9.0 r31).

Anybody experiencing this and/or have some ideas as to what can be done?  Thanks.

---

### Post by aysiu on 2007-06-04
I don't know what the problem is, but you can probably better diagnose it if you run Opera or Firefox from [the terminal](http://www.psychocats.net/ubuntu/terminal), visit a Flash website, and then see what error messages appear. Then, Google the error message.

Just type ```
firefox
``` or ```
opera
``` in the terminal.

---

### Post by Mike_88 on 2007-06-04
Hey, thanks for the tip, but the only output I get after running Firefox from the terminal is the following:

> ** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)

---

### Post by aysiu on 2007-06-04
One of these links may help:
[https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/104470](https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/104470)
[https://bugs.launchpad.net/gentoo/+source/liferea/+bug/98725](https://bugs.launchpad.net/gentoo/+source/liferea/+bug/98725)

---

### Post by Mike_88 on 2007-06-04
Well I have noticed that this problem seems to go beyond just Flash.  Once the problem begins, even simple audio files of various formats are unable to play properly.  Does this open the door to a potentially different issue?

---

### Post by luptinpitman on 2007-06-04
My machine is doing the same thing now.  Not getting any sound on flash vids and the movies/clips freeze every 2 or 3 seconds.  I can advance and rewind and it will play 2 or 3 seconds then freeze again.

This is not effecting DVD rips I have on my machine or audio files either.  Apparently specific to FF and flash.  I've removed/reinstalled flash via automatix (no fix).

This problem came about after yesterdays updates, though I didn't pay attention to what was updated :(.

Any help much appreciated.

---

### Post by Mike_88 on 2007-06-04
This is sounding identical to my problem, luptin.  It's certainly not specific to Firefox for me, since I can replicate it in Opera and now I have noticed that it affects audio files, thus it doesn't seem to have anything to do with upgrading Firefox to 2.0.0.4, but more likely the kernel upgrade.  Are you sure that this only happens to you in Firefox and flash videos?

---

### Post by luptinpitman on 2007-06-04
I was just about to install opera to verify for you when I decided to restart my FF session since I hadn't since uninstalling/reinstalling Flash via automatix.  Browser didn't start so I checked running processes and saw 2 instances of firefox-bin.  Killed both, launched FF and verified sound and no freezing on multiple sites including youtube.com.

Have you tried uninstall/reinstall of flash?  Seems to have been the fix for me as I made no other changes to the system.

---

### Post by Mike_88 on 2007-06-04
Yup, already tried reinstalling to no avail.

---

### Post by Mike_88 on 2007-06-04
This is definitely looking more and more like a sound issue.  I just noticed that when I am playing an audio or video file on my computer (for instance, using VLC), and I pause it but not close the player, no other audio will play, whether it be another file on my computer or a video on YouTube (in which case the video plays without sound).  Certainly wasn't experiencing this before.

---

### Post by luptinpitman on 2007-06-04
Mike, I actually saw a similar problem with the sound on a buddies machine.  Was quite some time ago, probably dapper, but I remember that we basically reconfigured ALSA and he never had the problem again.  I want to say we used something to do with alsa-utils or something like that.

Probably not the pinpoint help you were looking for but it's all I have :(

---

### Post by Mike_88 on 2007-06-04
No worries man, thanks for trying.  I'm sure someone will eventually come along that is familair with this problem.

*Proceeds to pray*

---

### Post by Mike_88 on 2007-06-05
Any further thoughts on this? My output from aplay-l is as follows:

> **** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC861 Analog [ALC861 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

---

### Post by tp21 on 2007-06-06
hi,
i confirm this bug with firefox. it happens with video flashes like youtube. but websites that use flash as navigation tools work fine(for example [www.alhamra.de](www.alhamra.de)). 
i didn't make the last updates, i have firefox 2.0.3, and kernel 2.6.20.15
thanx

---

### Post by Mike_88 on 2007-06-06
Hey, 
Thanks for confirming this.  It seems like it's only flash sites that use video that causes the problem for me too, and after it happens I seem to have audio problems playing any file, flash or otherwise.  Any further ideas out there?

---

### Post by tp21 on 2007-06-07
hi,
i also think that it is a sound problem. i am using an ibm thinkpad T21, the machine is suffering from a bug concerning sound: the sound doesn't function after suspend/resume cycle. now i relized that video flashes only freeze when i play them after resume, but playing them after a fresh start-up doesn't cause them to freeze. i tried this couple of times, and it is the same results.
bye

---

### Post by Mike_88 on 2007-06-12
*Bump*

Any further ideas out there?  It certainly seems to be a flash issue since I only notice it when viewing flash videos.

On another note, I have fixed the issue noted above in which aplay-l revealed two playback sources, with one being the modem.  Now, only the first appears, as follows:

```
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC861 Analog [ALC861 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

---

### Post by DagMan on 2007-06-12
For me it's not just Flash as it happened with embedded wma yesterday.  I'm using a toshiba laptop that needed a sound fix (search the forum for toshiba sound fix for details) and to get sound back after this happens, which I assume will work for others as well, I made a launcher that does the following:
kill $(lsof -t /dev/dsp* /dev/audio* /dev/mixer* /dev/snd/*)
I hate that there's a launcher on my panel to fix dead sound but for now it's what I've got.
Anyhow, I'm curious if others having this problem also have a system that needed an extra modification to get sound working, toshiba laptops etc etc.

---

### Post by Mike_88 on 2007-06-12
Well for what it's worth, I am running a Toshiba laptop as well, a Satelitte A100.  I had problems in Edgy with sound as well, and it too surrounded Flash, but it was even worse.  Sound has always seemed to work for me right after a fresh install, but Flash has been an endless pain.

---

