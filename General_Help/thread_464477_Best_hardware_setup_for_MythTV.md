---
title: "Best hardware setup for MythTV"
date: 2007-06-04
forum: General Help
---

### Post by DeathOnJuice on 2007-06-04
Hey, everyone. I just decided to build a PVR for a summer project, but I'm having a little bit of trouble. Here's the deal. I have a Wii with composite RCA output and a digital cable box with a coaxial cable output. I want to be able to have PVR functionality for the cable TV and lag-free recording for the Wii (as in, I want there to be no more delay than playing normally on a TV). For cable, I want to watch the output on the TV, but for the Wii, I would be fine with it on the monitor if it's not possible to play without lag on the TV. So, here are my questions:

1. Is this a good card for my purposes? What's the difference between it and the other PVR-150s on Amazon? [http://www.amazon.com/Hauppauge-WinTV-PVR-150-MCE-White-Tuner-Remote/dp/B000E65HOO/ref=pd_bbs_sr_2/104-4058530-9954341?ie=UTF8&s=electronics&qid=1180996238&sr=8-2](http://www.amazon.com/Hauppauge-WinTV-PVR-150-MCE-White-Tuner-Remote/dp/B000E65HOO/ref=pd_bbs_sr_2/104-4058530-9954341?ie=UTF8&s=electronics&qid=1180996238&sr=8-2)

2. If I ran My Wii's output into the TV Tuner and then to the TV (or even played it on the monitor), would there be noticeable lag while recording due to encoding, recording, decoding, and all that stuff? That would make it hard to play. If so, I'll convert it's RCA plugs into coaxial and split that, one signal to the TV and one to the computer to record. If I have to use the second method, could I still use MythTV to record it, or is there another good program? 

3. Is KnoppMyth a good choice for easy MythTV use?

Thanks so much for reading my long post!

---

### Post by tagra123 on 2007-06-04
I put my myth box together out of spare parts. If you already have a PVR XXX go ahead and use that, but if you need to buy one grab an old wintv card from ebay, They work fine and are a no fuss setup. WINTV-GO card is the name I believe..

Connecting sound and video is reallly not difficult - You can buy adapter or make your own and send the signal whereever you want.

Ubuntu is fairly easy to set up mythtv on now. Hardest part I thought was getting mysql to work with it -- I followed a guide that gave bad advice. I'd suggest using phpmyadmin to correct any database problems you may encounter. Perhaps this has been fixed already,

Ours is running on Breezy -- I think the uptime is around 70 days right now. We use it for a file server too.

---

### Post by DeathOnJuice on 2007-06-04
I updated my first post, tagra. Could you (and anyone else) take a look at it again? Thanks!

---

### Post by DeathOnJuice on 2007-06-04
I cut down the first post even more. I'm knocking out problems, but I still need help.

---

### Post by tagra123 on 2007-06-05
MythTV is not LIVE -- it has a ferw seconds delay.


I'd use a splitter, or make one, from the Wiil

                               -------------------- TV AV IN
                               |
WII---A/V Out-------|
                               |
                               -------------------- WinTV AV IN   (For Audo A RCA to Phono Jack adapter)

By doing this you can see the play live on the TV and Play It back later using the recording.

You may also be able to capture videot directly to the monitor using MPlayer (Google for this) You might even be able to do this while recording the programusing MythTV and mplayer at the same time with out the splitter.  Live TV for Myth is buffered (recorded) this is why you can pause and fast forward or rewind the live tv.

---

### Post by beerorkid on 2007-06-05
I have a pvr 250 and I use it just to capture, no myth.  use coaxial.
with the ivtv drivers in feisty it was too simple.

set to channel 3
```
ivtv-tune -c 3 -d /dev/video0
```
- of course change the "3" to the channel you need

to capture I just
```
cat /dev/video0 > filename.mpg
```
make sure to be in the directory you want the file to be saved in.  Otherwise do the path to it: /home/username/filename.mpg
You can make the extension what you want (as far as I know)

to watch TV 
```
mplayer -vo xv /dev/video0
```

all that from [here]("http://hyams.webhop.net/MythTV/myth_ubuntu.html") section 5

I just use the output of my cable DVR so no channel switching.
Even by doing it this way the lag is at least a second.

EDIT: Yeah that link goes to a guide for installing breezy mythtv, very old.  I just use those commands to do the bare minimum capture and do not use it that often, but works really well..

---

### Post by DeathOnJuice on 2007-06-05
Thanks, everyone! I think I have the information I need.

By the way, to anyone reading this thread, the rest of that guide is obsolete. The commands he described, however, are still fine to use.

---

### Post by tagra123 on 2007-06-05
Thanks  beerorkid .   I knew I'd seen a way to do that before.

---

