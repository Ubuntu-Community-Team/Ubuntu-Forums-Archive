---
title: "Broken sound on HP TC4200 tablet running 16.04 32 bit"
date: 2016-10-01
forum: General Help
---

### Post by cody16 on 2016-10-01
I've installed Ubuntu 16.04 32 bit on my HP TC4200 laptop, and then fully updated it.

My Original issue was that the sound was playing through the speakers and the headphones simultaneously.

 I've now figured out how to fix that original problem after playing around in the Ubuntu live cd environment. I simply had to go into alsamixer and unmute "Headphone Jack sense", which was muted/turned-off by default for some reason.

Anyway, while I was in the process of figuring out how to fix that original problem, I've completely messed up the sound on my copy of 16.04 that is actually installed on the hard drive.

First, I had tried to follow a guide that I found on Google which instructed me to install the linux realtek HD audio driver, which I did.
Doing so caused my audio device in the sound output applet to be replaced by a "Dummy Output" device, which played no audio at all.

I tried to fix the "Dummy output" error by uninstalling and reinstalling alsa-utils and pulseaudio, but that only made things much worse. Now I have no sound control at all, the slider is completely gone, alsamixer is missing, and the entire system settings applet will not launch.

I tried to fix that problem by completely reinstalling linux-image, and linux-image-generic, but that did no good.

when I try to launch alsamixer I get the following error:
```
cannot open mixer: No such file or directory
```

lshw reports that the multimedia device is UNCLAIMED.

"aplay -l" reports:
 ```
aplay: device_list:268: no soundcards found...
```

lsmod reports no snd modules loaded at all.
I can modprobe in the following snd modules:

```
snd_pcm                
snd_seq_midi           
snd_seq_midi_event     
snd_rawmidi            
snd_seq                
snd_seq_device         
snd_timer              
snd                    
soundcore
```

but when I try to modprobe in probably the most important snd modules:
```
snd_intel8x0 
snd_ac97_codec
ac97_bus
```

I just get the following error:
```
modprobe: FATAL: Module <mod_name> not found in directory /lib/modules/4.4.0-38-generic
```

I tried throwing all of these modules into /etc/modules, but those last three important modules still won't load.

---

### Post by cody16 on 2016-10-01
Well, I guess i'll just have to reinstall Ubuntu which I really didn't want to do. It took me like 3 hours to set up this install to be just the way I wanted it. Oh, well.

---

