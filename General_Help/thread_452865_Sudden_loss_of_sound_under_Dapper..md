---
title: "Sudden loss of sound under Dapper."
date: 2007-05-23
forum: General Help
---

### Post by andrew.46 on 2007-05-23
Hi,

 I have had a sudden loss of all sound while using Dapper, as if all sound has been muted. Just to exclude a hardware problem I ran the Live CD and sound is fine while running this.

 So there is a setting somewhere that has muted all sound but I cannot find it!!!

[LIST=1]
[*]Under 'Volume Control' / Preferences the device is Intel ICH5 (ALSA Mixer
[*]Under System / Preferences / Sound Play System Sounds is checked
[/LIST]

 Any ideas? I am heartened more than a little that the Live CD plays sound flawlessly.

                        Andrew

---

### Post by mlind on 2007-05-23
have you tried launching alsamixer from console and see if any channels are muted or have low volume?
If you create a new temporary user, does the volume work normally for this user?

---

### Post by andrew.46 on 2007-05-23
Hi,

 Thanks for your prompt reply:

> **mlind said:**
> have you tried launching alsamixer from console and see if any channels are muted or have low volume?
If you create a new temporary user, does the volume work normally for this user?

 I was not aware of alsamixer before and in fact as you suggested one of the channels was muted:

```
 Card: Intel ICH5                                                             
&#9474;&#9474; Chip: Analog Devices AD1981B                                                 
&#9474;&#9474; View: [Playback] Capture  All                                                
&#9474;&#9474; Item: Master Mono   
```

 As well as PCM channel, although I am not entirely clear what either of these involves :( Anyway I either turned on or increased volume in all channels and I have sound back!!

             Thanks very much for your help,

                        Andrew

---

