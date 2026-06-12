---
title: "Sound Problem"
date: 2008-02-03
forum: General Help
---

### Post by WIndsorcalgarian on 2008-02-03
I am fairly new to ubuntu, so when i upgraded from fiesty to gutsy i lost sound from everything, here is the soundcard i have:

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
Subsystem: Toshiba America Info Systems AC97 Data Fax SoftModem with SmartCP
Flags: bus master, fast devsel, latency 0, IRQ 22
Memory at d0340000 (64-bit, non-prefetchable) [size=16K]

any help would be appriciated

---

### Post by Metaljaz on 2008-02-03
Right click on the volume button in the top right hand corner. Open volume control and make sure that PCM is not muted. Mute PC speaker and Line in to start with.
Then again right click on the volume control button and select preferences. try selecting alsa mixer and then scroll down to PCM. Give that a try.

if all else fails try these troubleshooting threads/wiki:

[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

---

