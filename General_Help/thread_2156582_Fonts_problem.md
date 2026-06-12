---
title: "Fonts problem"
date: 2013-06-22
forum: General Help
---

### Post by linuxformat on 2013-06-22
Hi 

When i try to start moves from vlc and put it the arabic subtitles other language came  from other Planet :) it is look like this (  áã íÍÏË ÔÆ ãä åÐÇ ÃÈÏÇð- 
ãØáÞÇð- )  

I installed arabic language to the system but the main language it is EN and the same thing and sorry for my EN Weak.

Regards

---

### Post by Impavidus on 2013-06-22
That must be an encoding problem, with the subtitle file being in an arabic encoding and the player interpreting it as a latin encoding. Vlc must have an option somewhere to select the encoding (maybe labeled as character set) of the subtitle file. Else it may be possible to convert the encoding of the subtitle file to UTF-8, which should be recognised automatically (having been the default encoding on Linux for years).

I never encountered this problem myself, so I can't be very specific.

---

