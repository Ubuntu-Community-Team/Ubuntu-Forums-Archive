---
title: "How to activate sound on thinkpad x61?"
date: 2007-09-04
forum: General Help
---

### Post by seaborn on 2007-09-04
Hi,

   I'm still working on getting Feisty 64-bit running properly on my thinkpad x61 (non-tablet). I'm trying to get sound to work - the volume up,down, and mute buttons show a graphical display of the speaker increasing and decreasing, but I can't get the laptop speakers or the audio jack to work.

   I've tried several guides on how to get it to work, but I haven't had any success on this kernel (2.6.20-15). Is there anyone who has had any luck getting this going?

Thanks a lot

---

### Post by zeus77 on 2007-09-05
Perhaps you've already seen it, but there's quite a bit of discussion (including a few success stories) in this thread:
  [http://ubuntuforums.org/showthread.php?t=503233](http://ubuntuforums.org/showthread.php?t=503233)
If you can do without sound for another 6 weeks, my advice would be to wait for Gutsy to be released, as most reports indicate this will solve the wireless, sound, and video woes of the X61.

zeus77

---

### Post by cvaty on 2007-09-14
in gusty, on x61

after first set of updates after install
```

sudo apt-get update
sudo apt-get upgrade

```

if the volume applet isn't all ready in your gnome panel, add it
right click -> prefrences

HDA Intel (Alsa Mixer)
then choose PCM

after this:
system -> prefrences -> sound
in the devices tab
things should be set to autodetect
and then the bottom should be the same as in the previous prefrences

it then works for me.
this was done on a fresh install of gusty tribe 5, on a x61

---

