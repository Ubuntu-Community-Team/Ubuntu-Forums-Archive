---
title: "sound converter"
date: 2007-04-11
forum: General Help
---

### Post by cessna_89702 on 2007-04-11
any good sound converters that make it .ogg and not having to do each file one at a time. I have been using audacity and that takes a while going one by one. So any that can convert big files?

---

### Post by MyR on 2007-04-11
if you are using nautilus, you can use nautilus-script-audio-convert
just install that and nautilus-script-manager
then do

```
nautilus-script-manager enable ConvertAudioFile
```

restart nautilus then you can right click on the audio file you want to convert and choose the format.

---

### Post by cessna_89702 on 2007-04-11
alright i got it downloaded and figured rebooting would reset it but it didnt. so how do  I reset?

& it says im missing codecs if i try to use it now. but if i enter that command in the terminal it says please restart nautilus

---

### Post by srt4play on 2007-04-11
You could try out soundconverter in synaptic.

---

### Post by MyR on 2007-04-12
try installing some of the codecs listed here [http://packages.ubuntu.com/dapper/sound/nautilus-script-audio-convert]("http://packages.ubuntu.com/dapper/sound/nautilus-script-audio-convert")

---

### Post by MyR on 2007-04-12
also you can restart nautilus using
```
nautilus -q
```
i believe
hope this helps

---

### Post by cessna_89702 on 2007-04-14
thanks i have all my music converted now!!!

---

