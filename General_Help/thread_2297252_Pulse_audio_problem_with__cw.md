---
title: "Pulse audio problem with  cw"
date: 2015-10-02
forum: General Help
---

### Post by jean_pierre2 on 2015-10-02
Hi,  I am currently unable to generate a sound with cw. Can you help? ```
 $ echo ok | cw cw: PulseAudio output not available (device: ( default )) cw: OSS output not available (device: /dev/audio) 
```  Thank you

---

### Post by dino99 on 2015-10-02
here is your issue: ****** OSS output not available **********

so from 'synaptic' you can find some related 'oss' packages (like osspd-pulseaudio, but you may need to install an other one; do tests)
[http://unixcw.sourceforge.net/about.html](http://unixcw.sourceforge.net/about.html)

but first be sure of:
- bios set to 'hda', not 'ac97'
- jack(s) well plugged (strictly same color)
then 'paref' and/or 'pavucontrol' can help to adjust the settings

---

