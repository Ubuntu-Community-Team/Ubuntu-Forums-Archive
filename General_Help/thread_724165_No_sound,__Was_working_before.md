---
title: "No sound,  Was working before"
date: 2008-03-14
forum: General Help
---

### Post by NoTG on 2008-03-14
The sound was working yesterday before i shut the computer down for the night, and i started up in Ubuntu again today, and no sound. I havnt changed any settings, it just wont work. Nothing is muted.

  :confused::confused::confused:

---

### Post by Sef on 2008-03-14
1) What version of Ubuntu are you using?

2) What are your specs, including your sound card?

---

### Post by NoTG on 2008-03-14
Im using Ubuntu 7.10

My specs are:

AMD 5600 X2 2.8Ghz (Dual core)
4GB RAM
Soundblaster Audigy ( with 7.1 Surround Sound )
Nvidia 8600 512mb
320Gb HDD + 160Gb HDD (Multi boot with XP on the 320GB Drive)

---

### Post by NoTG on 2008-03-15
Help anyone???

---

### Post by mali2297 on 2008-03-15
Post the output of
```

lspci | grep [Aa]udio
aplay -l
cat /proc/asound/modules

```
(Copy/paste the commands to a terminal.)

I get a sense of deja vu. :-k

---

### Post by NoTG on 2008-03-15
Output:  
```
lspci | grep [Aa]udio
07:07.0 Multimedia audio controller: Creative Labs SB Audigy LS
```


```

 aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: VT82xx [HDA VIA VT82xx], device 0: ALC861VD Analog [ALC861VD Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: CA0106 [CA0106], device 0: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: CA0106 [CA0106], device 1: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: CA0106 [CA0106], device 2: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: CA0106 [CA0106], device 3: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

```
 cat /proc/asound/modules
 0 snd_hda_intel
 1 snd_ca0106
```


Ive had a sense of Deja Vu all day.

---

### Post by mali2297 on 2008-03-15
> **NoTG said:**
> Ive had a sense of Deja Vu all day.

Yes, it looks very similar to [this]("http://ubuntuforums.org/showthread.php?t=724483"). If I modify the instructions for your card...

Open the file /etc/modprobe.d/alsa-base with
```

sudo nano /etc/modprobe.d/alsa-base

```

At the end of the file, add these lines
```

options snd-**ca0106** index=0
options snd-hda-intel index=1

```
Save (Ctrl+o) and quit (Ctrl+x). Reboot.

---

### Post by NoTG on 2008-03-15
It worked perfectly!. Thank you :):):)

---

