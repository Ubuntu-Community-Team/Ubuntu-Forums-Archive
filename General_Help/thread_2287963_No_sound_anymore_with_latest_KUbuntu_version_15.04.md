---
title: "No sound anymore with latest KUbuntu version 15.04"
date: 2015-07-23
forum: General Help
---

### Post by andreas44 on 2015-07-23
[FONT=arial]Hello,
 
 
 I recently upgraded from Ubuntu 14.04 to 15.04 and cannot hear any sound anymore with the newest Ubuntu version! I surfed the web for many hours looking for people with the same problem and tried different things found on discussion forums, but nothing seems to work.
 
 
 I found this page and tried what is in there: [https://help.ubuntu.com/stable/ubuntu-help/sound-nosound.html](https://help.ubuntu.com/stable/ubuntu-help/sound-nosound.html)
 
 
 From my understanding, the soundcard is not detected anymore. When I type  ```
aplay -l
``` in the terminal, I get the message ```
[COLOR=#000000]aplay: device_list:268: no soundcards found...[/COLOR]
```

 Then, when I entered ```
lspci -v
``` I found the following information regarding the audio device:
 
 
 ```
[COLOR=#000000]00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition A[/COLOR]udio Controller (rev 05)[INDENT]Subsystem: Intel Corporation Device 2003 
[/INDENT]
[INDENT]Flags: bus master, fast devsel, latency 0, IRQ 35 
[/INDENT]
[INDENT]Memory at fe520000 (64-bit, non-prefetchable) [size=16K] 
[/INDENT]
[INDENT]Capabilities: <access denied> 
[/INDENT]
[INDENT]Kernel driver in use: snd_hda_intel
[/INDENT]

```  
 
 I'm not quite sure what to do next. In another discussion found of the web, they talk about &#8220;alsamixer&#8221;, however when I enter ```
/usr/bin/alsamixer
``` I get the message ```
[COLOR=#000000]cannot open mixer: No such file or directory [/COLOR]
```[COLOR=#000000](even though alsamixer is in the /usr/bin directory).[/COLOR]
 
 
 [COLOR=#000000]Where to go from here? Anyone has any idea?

Thanks!
[/COLOR][/FONT]

---

### Post by andreas44 on 2015-07-27
Nobody has any idea? :-(

---

### Post by SeijiSensei on 2015-07-27
Kubuntu 15.04 uses the new KDE5 platform which, to my mind, is still "not ready for prime time."  In KDE4, I would direct you to System Settings and the Multimedia applet there.  If that still exists in KDE5, you should be able to manage the audio subsystem there.

If you have multiple audio devices (like a speaker jack and audio via HDMI), I suggest installing **plasma-widget-veromix** as the volume control manager instead of KMix.  It makes it easy to switch among inputs and outputs and choose different profiles.

I'm sticking with Kubuntu 14.04 until at least 16.04 is released.

---

### Post by andreas44 on 2015-08-05
> **SeijiSensei said:**
> Kubuntu 15.04 uses the new KDE5 platform which, to my mind, is still "not ready for prime time."  In KDE4, I would direct you to System Settings and the Multimedia applet there.  If that still exists in KDE5, you should be able to manage the audio subsystem there.

If you have multiple audio devices (like a speaker jack and audio via HDMI), I suggest installing **plasma-widget-veromix** as the volume control manager instead of KMix.  It makes it easy to switch among inputs and outputs and choose different profiles.

I'm sticking with Kubuntu 14.04 until at least 16.04 is released.

Thanks for the suggestions, but the problem turned out to be something completely different than what I expected (I am not really good with computers and have to rely a lot on my colleagues). My computer is part of a cluster and I log-in with my username which has no admin rights. I found out yesterday that I couldn't open the folder of a USB stick on my computer. One of my colleagues added the following line

```
session required    pam_systemd.so
```

in the /etc/pam.d/sddm file. This not only solved the USB stick issue, but also the sound issue!

---

