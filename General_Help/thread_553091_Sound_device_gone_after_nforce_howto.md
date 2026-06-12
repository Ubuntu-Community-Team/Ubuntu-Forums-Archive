---
title: "Sound device gone after nforce howto"
date: 2007-09-17
forum: General Help
---

### Post by kingmob on 2007-09-17
Since i had a problem with low volume (almost nonexistent even) i tried [this](https://help.ubuntu.com/community/HdaIntelSoundHowto) to fix it. However, after rebooting and trying 
```
cat /proc/asound/card0/codec#* | grep Codec
```
I found out i did not have the directory asound. Further inspection showed me that the sound device is completely gone! Can't select it in alsamixer nor the sound preferences. The chipset is listed in lspci -v as:
```

00:04.0 Multimedia audio controller: nVidia Corporation CK804 AC'97 Audio Controller (rev a2)
        Subsystem: EPoX Computer Co., Ltd. Unknown device 1011
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 12
        I/O ports at f000 [size=256]
        I/O ports at ec00 [size=256]
        Memory at fe02d000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

```

I can't seem to find what to do now. I'm not sure why the card has disappeared and i don't know how to add it manually. I also don't know how to get back to my original setup, since it used to work fine.

---

