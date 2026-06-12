---
title: "Sound is faint"
date: 2008-03-04
forum: General Help
---

### Post by Kralizec on 2008-03-04
I have a strange problem with the sound on a Ubuntu desktop that I built. I'm not sure whether the problem lies in my configuration or my hardware. Here's the information I believe to be relevant:

[LIST]
[*]I have the most recent version of Alsa installed.
[*]All Alsa channels are at maximum volume.
[*]I have an ECS Elitegroup HT 1600 Micro ATX motherboard with on-board graphics card, Ethernet, USB, and speaker/mic jacks.
[*]I have a (rather cheap) case with built-in speaker/mic jacks.
[/LIST]

Here is the problem: with the speakers at maximum volume, the only audio that can be heard from either speaker jacks is a large amount of static and the correct audio very  very faint in the background. I have tested the audio using a LiveCD with the same result.

Up until a short time ago the front jack worked perfectly and when I initially built and configured the machine the rear jack worked perfectly as well. I don't know for sure what has been done to the machine directly before the sound stopped working properly, as my girlfriend is the primary user of the machine.

I really hope this isn't a hardware problem as I can't afford to buy a new motherboard.
If anyone needs any more information in order to help, just ask.

---

### Post by LuisGMarine on 2008-03-04
Go ahead and run this command, and paste the output:
```

lshw -C multimedia
```

I was having the same issue as far as low sound, but recompiling my alsa drivers, and messing arond my alsa-base config fixed the problem for me.  Let's see if we can do the same for you.  

:guitar:

---

### Post by Kralizec on 2008-03-04
This is the output:

```

*-multimedia            
       description: Multimedia audio controller
       product: MCP51 AC97 Audio Controller
       vendor: nVidia Corporation
       physical id: 10.2
       bus info: pci@0000:00:10.2
       version: a2
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list
       configuration: driver=Intel ICH latency=0 maxlatency=5 mingnt=2 module=snd_intel8x0
```

---

### Post by LuisGMarine on 2008-03-04
Try this link:

[http://ubuntuforums.org/showthread.php?t=363365](http://ubuntuforums.org/showthread.php?t=363365)

I'll look further into the matter tomorrow, I have to get to bed to be up for work.  If that link doesn't fix it then let me know so I can attempt to help you fix it.

Cheers! :guitar:

---

### Post by Kralizec on 2008-03-08
Went through a lot in that thread. Nothing worked. One key difference between my problem and the one in that post, however, is that aplay -l yields output for me:

```

~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: ICH [Intel ICH], device 0: Intel ICH [Intel ICH]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: ICH [Intel ICH], device 2: Intel ICH - IEC958 [Intel ICH - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```
One more thing: I get the same problem using different speakers, so its not the speakers that are the problem.

---

