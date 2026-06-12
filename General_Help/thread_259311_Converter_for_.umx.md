---
title: "Converter for .umx ?"
date: 2006-09-17
forum: General Help
---

### Post by Unknowndeepness on 2006-09-17
Simple question:
Can i convert umx files into ogg and wav in ubuntu?

If so, how can i do that?

---

### Post by bugzor on 2006-09-17
get xmms,xmms oggrec and xmms-modplug

```
sudo apt-get install xmms xmms-oggre xmms-modplug
```

run xmms and go to settings and select audio output to og(g)re (or diskwriter if you want them to .wav)
and deselect 'mikmod' and select modplug (and configure it so you get somewhat better quality)

then just load .umx files to xmms playlist and 'play' them
and they will be converted to .ogg to your home folder (take repeat and shuffle off otherwise it will convert them again and again and again...)

---

