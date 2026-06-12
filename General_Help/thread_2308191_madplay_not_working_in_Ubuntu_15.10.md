---
title: "madplay not working in Ubuntu 15.10"
date: 2016-01-01
forum: General Help
---

### Post by Anes_P_A on 2016-01-01
Dear Friends,
I am using Daisy-player in Ubuntu 15.10. I am installed madplay in it. But when I run it got error in terminal as

> 
anes@hackernet:~/Music/Mahathcharithamaala$ madplay -v /home/anes/Music/Mahathcharithamaala/aud033.mp3 
MPEG Audio Decoder 0.15.2 (beta) - Copyright (C) 2000-2004 Robert Leslie et al.
audio: No such file or directory


I could not find a solution for 4 hour search yet . Please help me with a solution.

Thanks
Anes

---

### Post by Anes_P_A on 2016-01-03
Dear friends,
Got the solution. The problem of this may be different for different user. So do the following 3 steps ( Third step is different for different users)

a) sudo apt-get purge existing madplay
b) get madplay source, ./configure, make and sudo make install
c) Here got any specific problem , rectify it  (e.g: install osspd packages)

then got the working system

All the Best

Anes

---

