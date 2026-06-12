---
title: "sound not working"
date: 2006-10-27
forum: General Help
---

### Post by Zandaa on 2006-10-27
okay, so heres the deal, I updated to Edgy Eft yesterday on my 64-bit machine (running a 64-bit Edgy now), the sound was working fine yesterday, but now all of a sudden the sound isnt working anymore :S any methods I can use to pinpoint/resolve this problem?

(btw. Im using the on-board soundcard on my ASRock 939 DUAL-VSTA motherboard)

---

### Post by Kateikyoushi on 2006-10-27
Follow this guide to find out what went wrong. [LINK]("http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide")

If you get stuck post the output of these commands.
```
aplay -l
lspci -v
```

---

### Post by Zandaa on 2006-10-27
okay, the aplay -l gives the following output:
```

zandaa@z-1server:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 2: default [PnP Audio Device        ], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

lspci -v does not list the detected device, however in System>Preferences>Sound I found out that the default card-output had changed from the in this case standard PnP-Audio device to a SAA7134, which I believe is the sound output on my TV-card-tuner... so, I believe this fixes it, even though OSS cant open the resource for writing to... sound works, for now.. I do not know however what managed to make it switch from one default to another without me touching those settings...

---

