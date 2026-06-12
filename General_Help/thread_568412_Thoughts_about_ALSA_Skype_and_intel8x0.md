---
title: "Thoughts about ALSA Skype and intel8x0"
date: 2007-10-05
forum: General Help
---

### Post by vhof on 2007-10-05
Hi,
I succeded to make intel8x0 drivers work, I don't know exactly how, just uninstalled and installed it couple of times, compiled ALSA source etc.
The insteresting part is that after all those procedures with the help of Duplucate Front function in volume control I'm able to hear sound on rear speakers.
The problem was with Skype - no sound was there. After some useless playing I found [this]("https://help.ubuntu.com/community/Skype"), and after the following instructions and nothing more except restarting Ubuntu:
```

Create or add the following to your .asoundrc file:

gedit ~.asoundrc

Add the following text to it

pcm.skype {
   type asym
   playback.pcm "skypeout"
   capture.pcm "skypein"
}

pcm.skypein {
   # Convert from 8-bit unsigned mono (default format set by aoss when
   # /dev/dsp is opened) to 16-bit signed stereo (expected by dsnoop)
   #
   # We can't just use a "plug" plugin because although the open will
   # succeed, the buffer sizes will be wrong and we'll hear no sound at
   # all.
   type route
   slave {
      pcm "skypedsnoop"
      format S16_LE
   }
   ttable {
      0 {0 0.5}
      1 {0 0.5}
   }
}

pcm.skypeout {
   # Just pass this on to the system dmix
   type plug
   slave {
      pcm "dmix"
   }
}

pcm.skypedsnoop {
   type dsnoop
   ipc_key 1133
   slave {
      # "Magic" buffer values to get skype audio to work
      # If these are not set, opening /dev/dsp succeeds but no sound
      # will be heard. According to the alsa developers this is due
      # to skype abusing the OSS API.
      pcm "hw:0,0"
      period_size 256
      periods 16
      buffer_size 16384
   }
   bindings {
      0 0
   }
}


```

Skype works. 
Please confirm this problem, or pour your thoughts on this subject.
Thanks.

---

