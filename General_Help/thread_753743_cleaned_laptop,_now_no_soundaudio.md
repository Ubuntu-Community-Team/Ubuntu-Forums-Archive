---
title: "cleaned laptop, now no sound/audio"
date: 2008-04-13
forum: General Help
---

### Post by Th3Professor on 2008-04-13
I just took apart the laptop... removed the dust/etc. that had collected inside it (to help prevent the laptop from overheating).

Now there's no sound. I can take it apart again and make sure everything's hooked up.

However, what kinds of tests can I perform with the computer on before doing that?

Thanks!

EDIT:
p.s.- also, after logging in, I can click (hilite) items on the desktop, though after a moment it doesn't let me click on them anymore. I can still access the menu (apps/places/system/etc.) and even menus inside of programs, just not the desktop. Any ideas how I can make it let me click on the desktop items again?

---

### Post by 1/0 on 2008-04-13
It sounds to me as a button being stuck. Check that but I would open it again.

---

### Post by Th3Professor on 2008-04-14
Which button do you refer to?

Here's an update:
The audio is, physically, working. I booted into another operating system and the sound was working perfect... music, OS sounds, movie audio, etc. all worked.

How might I correct the audio within Ubuntu? (Thankfully it won't require opening up again.)

Oddly, it's Ubuntu Studio, aka audio = really important. Go figure sound goes off. lol ;)

---

### Post by 1/0 on 2008-04-14
Well then its no button stuck. 

Are you dual booting with windows? I've actually  heard of cases where if you unmute the sound in windows and it gets unmuted in Ubuntu. But I don't use windows. 
You could try opening gnome-volume-control. Then go “Edit” - “Preference”. Check “Headphone Jack Sense” and “Line Jack Sense”.

Goto “Switch” tab, Uncheck both of them. 

That might do the trick. 

Btw. Can you see the card when issuing "aplay -l"?

---

### Post by Th3Professor on 2008-04-15
Okay, I did those things (in the volume control). The sound was not muted on the WinXP partition.

Still no sound. :(

Here's the aplay -l output:
```
**** List of PLAYBACK Hardware Devices ****
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 0: Intel ICH [Intel 82801DB-ICH4]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 4: Intel ICH - IEC958 [Intel 82801DB-ICH4 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

Here is autoplay -L output:
```
default:CARD=I82801DBICH4
    Intel 82801DB-ICH4, Intel 82801DB-ICH4
    Default Audio Device
front:CARD=I82801DBICH4,DEV=0
    Intel 82801DB-ICH4, Intel 82801DB-ICH4
    Front speakers
surround40:CARD=I82801DBICH4,DEV=0
    Intel 82801DB-ICH4, Intel 82801DB-ICH4
    4.0 Surround output to Front and Rear speakers
surround41:CARD=I82801DBICH4,DEV=0
    Intel 82801DB-ICH4, Intel 82801DB-ICH4
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=I82801DBICH4,DEV=0
    Intel 82801DB-ICH4, Intel 82801DB-ICH4
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=I82801DBICH4,DEV=0
    Intel 82801DB-ICH4, Intel 82801DB-ICH4
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
null
    Discard all samples (playback) or generate zero samples (capture)

```

---

### Post by Th3Professor on 2008-04-16
No sound... any help's appreciated.

---

