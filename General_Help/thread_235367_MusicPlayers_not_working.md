---
title: "MusicPlayers not working"
date: 2006-08-13
forum: General Help
---

### Post by BrokenArrows on 2006-08-13
This started happening after i followed the instructions to fix Sound on Flash in Firefox here [http://ubuntuforums.org/showthread.php?t=75237](http://ubuntuforums.org/showthread.php?t=75237)

The sound in the flash now works fine but now i cannot play mp3 sound files on my computer.

When i try and play an mp3 using Rhythmbox or any other music application i get the following error;

"Could not open the resource for writing"

When i try and play a file with Totem i get the same error as above and this is the output from the console:

```
(totem:7659): GLib-GObject-WARNING **: gsignal.c:1716: signal
`got-redirect' is invalid for instance `0x8319cc8' - using device default -
using device default ALSA lib conf.c:1566:(snd_config_load1)
_toplevel_:34:0:Unexpected char ALSA lib conf.c:2811:(snd_config_hook_load) 
/etc/asound.conf may be old or corrupted: consider to remove or fix it ALSA lib conf.c:2672:(snd_config_hooks_call) function snd_config_hook_load
returned error: Unknown error ALSA lib conf.c:3040:(snd_config_update_r) hooks failed, removing configuration
```

---

