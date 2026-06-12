---
title: "[SOLVED] I can no longer play wav or mid(midi) files!"
date: 2008-05-05
forum: General Help
---

### Post by Rytron on 2008-05-05
Hi,
I no longer can play wav or mid(midi) files. There is not problem with any other music formats though. Any ideas?
Thanks.

---

### Post by erginemr on 2008-05-05
I assume you have already installed a midi synthesizer to your system:
[https://wiki.ubuntu.com/MidiSoftwareSynthesisHowTo](https://wiki.ubuntu.com/MidiSoftwareSynthesisHowTo)

---

### Post by Rytron on 2008-05-05
> **erginemr said:**
> I assume you have already installed a midi synthesizer to your system:
[https://wiki.ubuntu.com/MidiSoftwareSynthesisHowTo](https://wiki.ubuntu.com/MidiSoftwareSynthesisHowTo)

Hi,
No I have not installed a midi synthesizer.
The strange thing is that I used to be able to play all music files including wav and midi(mid) before. I must have inadvertently changed a setting that has stopped me playing wav and midi files.

---

### Post by Rytron on 2008-05-05
Hi, I can now play .wav files. A restart must have solved that. I will try to install TiMidity++ to play midi(mid) files. 
Cheers.

---

### Post by Rytron on 2008-05-05
I got Timidity from Synaptic instead of the link. It is big (around 27mb).
I can now play midi files.

Thank you erginemr.

---

### Post by erginemr on 2008-05-05
You are welcome. :D

I can propose you to extend your efforts in a two-pronged research:

(1) Your sound card may support wave table synthesis (e.g. SB Live!, SB Audigy, etc.), in which case you won't need software sysnthesis to play midi:
[https://help.ubuntu.com/community/SoundcardsWithHardwareSynth](https://help.ubuntu.com/community/SoundcardsWithHardwareSynth)
[https://help.ubuntu.com/community/Midi/HardwareSynthesisSetup](https://help.ubuntu.com/community/Midi/HardwareSynthesisSetup)

(2) Otherwise, the default sound font coming with Timidity (called Freepats) is (to my knowledge) still being developed and there are better sound fonts out there. One of the better is "Fluid R3" with extraordinary sound quality at the cost of extra hard drive space (some 140 MB):
[http://wiki.archlinux.org/index.php/Timidity](http://wiki.archlinux.org/index.php/Timidity)
[http://ubuntuforums.org/showthread.php?t=400323](http://ubuntuforums.org/showthread.php?t=400323)

(3) If you like Timidity, you can also consider installing the package "timidity-interfaces-extra" from synaptic, which installs a few graphical frontends to it. So, you can play music files via Timidity GUI just like any other Gnome music player.

---

