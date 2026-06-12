---
title: "rpi 4 alsamixer no file  no sound on hdmi"
date: 2020-07-16
forum: General Help
---

### Post by tjerram on 2020-07-16
i installed mate on an 8gb rpi 4 it woks but I have no sound from hdmi.  I have tried a bunch of solutions I found by googling it but no luck.  One consistent message I get is alasmixer no file of directory.  when I loo in sound settings there is no hardware listed.  I have had sound from Bluetooth headphones so there is a sound card somewhere.  As yo can tel I am A noob. any elp would be apprciated.

thanks

---

### Post by Holger_Gehrke on 2020-07-18
Which version of Ubuntu-MATE did you install ? The one I got from ubuntu-mate.org just two day ago is named 'ubuntu-mate-20.04-beta1-desktop-arm64+raspi.img.xz'. 

If I click on the loudspeaker-icon in the top panel and select sound settings from the menu, I can select between two alternatives on the output tab, both named 'Built-in Audio Stereo'. For me the top one produces sound on the AV-jack while the bottom one gives sound via HDMI.

The mixer-program you're trying to use is named 'al**sa**mixer', not 'al**as**mixer' (alsa is an abbreviation for Advanced Linux Sound Architecture; that's the low-level sound interface; in general there's also some kind of sound-server sitting on top of alsa, for most Ubuntu variants that's PulseAudio). If you use alsamixer, you'll find that the two sound outputs are seen as separate sound-cards, so you'll need to use function key 'F6' to switch between them.

Bluetooth is a completely different thing. A sound card (at least a modern one; old sound cards had actual synthesizer chips to make music with) is something that transforms digital samples into sound, with Bluetooth that happens in a DSP in the headphones, so in a way the headphones are the soundcard ...

Holger

---

