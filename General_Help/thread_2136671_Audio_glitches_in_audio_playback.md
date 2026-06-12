---
title: "Audio glitches in audio playback"
date: 2013-04-18
forum: General Help
---

### Post by NertSkull on 2013-04-18
I don't know how to document this problem, but when I listen to anything audio on my computer (Kubuntu 12.04) it get weird glitches where the sound shoots up, but only for like 2-5 milliseconds.  It kind of sounds like when you used to listen to CDs and they had a scratch on them.  

It happens in youtube, in grooveshark, in Guayadeque(mp3 player), any sort of sound.  I can click the volume meter in the panel, and watch it.  And you can see the slider jump from 20% up to 100% and back down to 20%.  It happens in a flash, but its enough to be annoying.  It probably happens 5-8 times every minute.

But its definitely doing it all the time.  Not just when I'm listening to music.  I just can't hear it do it if music/sound isn't playing.  But if nothing is playing, but I watch the volume bar, it still flashes up and down every so often.

It makes listening to any sound on my computer unbearable.  Its really not good.  What can I do to fix this.

I don't think I've installed anything weird for sound stuff.  Just a basic Kubuntu installation.

Any ideas?  thanks

---

### Post by dabl on 2013-04-18
Sound troubleshooting begins by getting the detailed information about your hardware, installed system, and driver version, as per:

[https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

```

cd ~/
  wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh
```

With that report available, google may help find the issue.  It sounds to me like something about your computer hardware is not completely stable, as this is not a commonly-reported problem. For example an unstable power supply circuit could conceivable cause voltage changes.

---

