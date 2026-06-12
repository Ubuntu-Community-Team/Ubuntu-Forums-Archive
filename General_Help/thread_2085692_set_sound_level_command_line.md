---
title: "set sound level command line"
date: 2012-11-18
forum: General Help
---

### Post by spiritech on 2012-11-18
i am trying to set the sound level using a command. i have tried most of the alsamixer options found over the web. i am using the optical out for sound output. when i run alsamixer and hit F6 the device is not listed.

spiritech

---

### Post by Yellow Pasque on 2012-11-18
1. Make sure pulseaudio-utils package is installed
2. Figure out which index the digital sink is (probably will be one)
```
pactl list sinks
```
3. Set the volume
```
pactl set-sink-volume SINK VOLUME
```
> Set the volume of the specified sink (identified by its symbolic name or numerical index). VOLUME can be specified as an integer (e.g. 2000, 16384), a linear factor (e.g. 0.4, 1.100), a percentage (e.g. 10%, 100%) or a decibel value (e.g. 0dB, 20dB). If the volume specification start with a + or - the volume adjustment will be relative to the current sink volume.

Example, set sink 0 to 50%
```
pactl set-sink-volume 0 50%
```

---

### Post by spiritech on 2012-11-19
> **Temüjin said:**
> 1. Make sure pulseaudio-utils package is installed
2. Figure out which index the digital sink is (probably will be one)
```
pactl list sinks
```3. Set the volume
```
pactl set-sink-volume SINK VOLUME
```

```
pactl set-sink-volume 0 50%
```

thankyou. the above code worked for me

---

