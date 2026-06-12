---
title: "Sound output problem (cannot use only one speaker)"
date: 2008-05-27
forum: General Help
---

### Post by Silent Ninja on 2008-05-27
This is the thing, one of my speakers are broken but i don't want to buy a new one (i'm at work, not on my home). On windows i had a little bar to check that all sound comes up from one of the speakers, but on linux when I do that, it just mutes the sound from the second speaker, doesn't send it thru the one that actually works. 

Is there any way to output all sound via one speaker? Like it was a mono sound card instead of a stereo one.

---

### Post by Norri on 2008-09-13
I have the same issue, help?

---

### Post by Silent Ninja on 2008-09-13
Come on, is it that hard to use the left speaker as the left speaker AND the right speaker too ?

---

### Post by panayk on 2008-09-13
I use /etc/asound.conf to define a device for virtual surround (upmix 2 channels to 6). You can try a modified version:

```
pcm.all_to_left {
    type route
    slave.pcm front
    slave.channels 2
    ttable.0.0 0.5
    ttable.1.0 0.5
    ttable.0.1 0
    ttable.1.1 0
}

pcm.!default pcm.all_to_left

```

The idea is that "ttable.x.y z" selects the percentage z that channel x in the new device will will contribute to channel y in the original device. So in our case: send 50% from the left channel and 50% from the right channel to the left speaker. My original configuration file was: 
```

pcm.vsurround51 {
    type route
    slave.pcm surround51
    slave.channels 6
    ttable.0.0 1
    ttable.1.1 1
    ttable.0.2 1
    ttable.1.3 1
    ttable.0.4 0.5
    ttable.1.4 0.5
    ttable.0.5 0.5
    ttable.1.5 0.5
}

pcm.!default pcm.vsurround51

```
It will probably take some trying before you can get it working. You can use "aplay -L" to list the available PCM's and "speaker-test -c <number of channels>" to find out which number is what speaker. Don't forget to restart alsa.

---

