---
title: "How to Convert tiff to jpeg"
date: 2013-03-10
forum: General Help
---

### Post by borgward on 2013-03-10
How to I convert tiff to jpeg? Is there an application that will do this?

---

### Post by Absolute Terror on 2013-03-10
You can do this with GIMP. It should be in Ubuntu Software Center.

---

### Post by borgward on 2013-03-10
I am looking for a stand alone application to do this. For example, I have tiff image on usb stick that came off of a mac. I just want a tool that will convert it to jpeg. I do not want to have to bring up gimp and poke around thru it just to do a simple chore.

I have "Sound Converter" that does a similar chore like if I want to send somebody a sound file that is .wav. I simply use sound converter to easily convert it to .mp3 so I can email it. I know I could do that with Audacity, but thats just too much trouble to convert 1 file.

---

### Post by Vaphell on 2013-03-10
default image viewer offers save as... on right click

if you need batch jobs look at imagemagick package (*convert* command would be the one you want), though you would need to get your hands dirty in terminal. That's not a bad thing though as these tools are so powerful, gui is pretty much impossible.

---

### Post by borgward on 2013-03-10
Thanks. That wasn't so painful. I just tried Imagemagic, but it was not quick and dirty. Did not want to cooperate. Permission denied.

---

### Post by Vaphell on 2013-03-10
i suspect you don't have permission to write on usb or something. Does it work when you copy it to your $HOME or by using some other path for destination file, eg

```
convert source.tif ~/converted.jpg
```

---

### Post by borgward on 2013-03-11
Yeah, I can copy to the stick, save to Home, etc. I can not do that with Image Majic.

---

