---
title: "After kernel update issue with recognizing video board and ethernet board"
date: 2018-04-16
forum: General Help
---

### Post by saurian2 on 2018-04-16
Hello,

Since the last few days I keep having an issue with Ubuntu 16.04. When I start my laptop the video board isn't recognized anymore and also the ethernet board. When this issue appeared I had 4.4.0-119 kernel linux image. Choosing to start from 4.4.0-116 things seemed to work ok. So I removed 4.4.0-119 to start directly 4.4.0-116. But even with this kernel it seems that my boards are not recognized and I actually have to choose in Grub the version 4.4.0-116 to work (which is weird because currently this is the only installed version). Now even this little trick didn't work and I had to choose as boot option 4.4.0-116 (upstart). Anyone knows what ca I do to fix this? There wasn't any problem like this before. Recently I deleted older kernels (4.4.0-xxx < 116). Could this be the problem? 

Thanks.

Best regards,
Sorin

---

