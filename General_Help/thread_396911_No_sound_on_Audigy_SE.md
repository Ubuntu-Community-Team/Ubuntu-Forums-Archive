---
title: "No sound on Audigy SE"
date: 2007-03-30
forum: General Help
---

### Post by Particle on 2007-03-30
Any help would be appreciated.

I don't get any sound when using my Audigy SE.  I've set the system to use it instead of the onboard like I always have in the past, but I still don't get sound.  I'm using a livecd of 7.04 beta 4 and have updated all alsa and totem related stuff.  **Downloading the final product is not an option, as my machine's OS is currently dead.  While using this livecd, I can't burn discs naturally.  This was the latest product I had and that god I did or I'd be without a machine for a while.**  Any pointers on getting sound working?

---

### Post by razi3l on 2007-10-12
replace your .asoundrc file with this script:



################################################## #######
#This is the standard setting (see: "!default")
#This profile, the default loaded, upmixes stereo sound to 5.1.

pcm.!default {
type plug
slave.pcm "surround51"
slave.channels 6
route_policy duplicate
}
################################################## ######
#This is the normal spdif output profile (optical, toslink).

pcm.!spdif {
type plug
slave.pcm "hw:0,1"
}

################################################## #####
#This is what one could call the "factory default setting", in other words, it only plays the actual channels. so if you fx want to watch a 5.1 movie, on the analog output, this is the option you want.


pcm.analog {
type plug
slave analog_slave;
}

pcm_slave.analog_slave {
pcm surround51;
format S32_LE;
}


save it, log out and back in.. you should have 5.1 surround!

---

