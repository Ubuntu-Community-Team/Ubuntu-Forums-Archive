---
title: "help me"
date: 2005-09-06
forum: General Help
---

### Post by pakistan00000 on 2005-09-06
hi friends plz help me .when i open ubuntu 5.04 media player it give me a massage not install plugins software. plz tell me where i download this plugins software

---

### Post by Weav on 2005-09-06
[QUOTE=pakistan00000]hi friends plz help me .when i open ubuntu 5.04 media player it give me a massage not install plugins software. plz tell me where i download this plugins software[/QUOTE]
read through this entire guide. It will give you most if not all the informatino you need.

[www.ubuntuguide.org](www.ubuntuguide.org)

---

### Post by bored2k on 2005-09-06
[QUOTE=pakistan00000]hi friends plz help me .when i open ubuntu 5.04 media player it give me a massage not install plugins software. plz tell me where i download this plugins software[/QUOTE]
 Execute the commands in **Terminal **mode (Applications -> System Tools -> Terminal)
1. ```
http://ubuntuguide.org/#extrarepositories
``` 
2. ```
sudo apt-get update
``` 
3. ```
sudo apt-get install totem-xine
``` 
4. ```
sudo apt-get install gstreamer0.8-plugins libdvdcss2 gstreamer0.8-lame gstreamer0.8-ffmpeg w32codecs libdivx4linux  ffmpeg mjpegtools vorbis-tools lame sox

``` 
5. ```
gst-register-0.8
```

---

