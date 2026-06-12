---
title: "video problems"
date: 2007-07-16
forum: General Help
---

### Post by cptjaben on 2007-07-16
I've been having problems playing videos on my computer lately, I've tried VLC as well as others, and when the vidoe plays it is either very chopping and jutty as is the case with .avi and .mpg or has no sound which is the case for .wmv. Does anyone know what might fix this or what codec should be installed, I used automatix and easyubnutu to install some of them. Thanks

---

### Post by mithion on 2007-07-16
I like gxine.  Have you tried using that program along with the gxineplugin package which contain support for extra restricted formats?

---

### Post by danhm on 2007-07-16
In my experience, VLC isn't the greatest at playing WMVs -- I like mplayer for that format.

Also, make sure you have all of the proper video codecs installed!

```
sudo apt-get install ubuntu-restricted-extras libxine-extracodecs
```

You might also want to install the w32codecs package (from the Medibuntu/PLF repo), but that may or may not be illegal.

---

