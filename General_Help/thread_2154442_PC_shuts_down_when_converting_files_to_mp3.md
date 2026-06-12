---
title: "PC shuts down when converting files to mp3"
date: 2013-06-14
forum: General Help
---

### Post by marco-stella2 on 2013-06-14
When I use Sound Converter or Soundkorverter to convert .ogg files to mp3, during the process the pc shuts down. Is it a software or hardware problem? It seems to happen only when I do that.

---

### Post by SuperFreak on 2013-06-14
Perhaps Sound Converter has an option ticked to shut down once the conversion process is completed (look in Preferences or options)

---

### Post by HiImTye on 2013-06-14
try it with ffmpeg
```
sudo apt-get install ffmpeg
ffmpeg -i /input/file.ogg -acodec libmp3lame /output/file.mp3
```[CENTER][COLOR=#333333][FONT=Roboto][/FONT][/COLOR][/CENTER]

---

### Post by QIII on 2013-06-14
Hello!

What sort of hardware are you running?  How CPU intensive is the process?  Have you monitored your CPU temperature?

Thanks.

---

### Post by marco-stella2 on 2013-06-15
Thank you, but it seems that there is no option like that.

---

### Post by marco-stella2 on 2013-06-15
How can I check the temperature? What do you need to know about the hardware? The processor is Intel® Core&#8482; i3 CPU M 380 @ 2.53GHz × 4, the pc is a Samsung R540. The operating system is Ubuntu 12.04.

---

