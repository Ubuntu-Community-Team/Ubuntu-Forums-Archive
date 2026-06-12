---
title: "Weird Sound Problem."
date: 2007-12-29
forum: General Help
---

### Post by penguinchrissy on 2007-12-29
I have a Dell laptop and I just installed 7.10 after having a lot of problems upgrading from Feisty. I had no problems in Feisty with my sound everything worked fine. When I upgraded it sounded like I blew my speakers. I tried playing some MP3s and the same thing sounded like my speakers were blowin. So I muted it and this is were it got weird I could still hear sound even though I had it muted. Changing  the volume does have an effect but its very little so I went to the volume control. After muting and unmuting everything I found all the sound was coming out of the PCM line. This seems to be where all the beeps and other good computer sounds are supposed to come out. How do I get my sound to come out of the main line like it should be? Everything is stock for an Inspiron 9300.

Somethings that might help. When main line is muted anything sounds muffled but is clear. When PCM is muted there is no sound what so ever even if the main line is at max.

---

### Post by danwood76 on 2007-12-29
You probably need to update the alsa drivers.
I found the ones in gutsy to be quite outdated/buggy a lot of people have had problems with them.

I would reccomend compiling the drivers from source, although this is quite daunting for most ubuntu users.

[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

this wiki has good sound troubleshooting guides, it also has ways of compiling from source, I reccomend getting the latest drivers from the alsa-project website and following the steps in the 'Using drivers from alsa-project' section.

regards,
Danny

---

### Post by drakebahamut on 2008-01-01
i just had the exact same problem go to this site and it should help make sure to restart your comp after doing step (fixing the problem) 

[http://linux.dsplabs.com.au/no-volume-control-gstreamer-plugins-and-or-devices-found-no-sound-or-voume-control-bug-on-ubuntu-p31/](http://linux.dsplabs.com.au/no-volume-control-gstreamer-plugins-and-or-devices-found-no-sound-or-voume-control-bug-on-ubuntu-p31/)


or just try putting this in to your shell terminal. it is one of the steps that should solve it if not use the l;ink

 sudo apt-get install linux-ubuntu-modules-2.6.22-14-386

---

