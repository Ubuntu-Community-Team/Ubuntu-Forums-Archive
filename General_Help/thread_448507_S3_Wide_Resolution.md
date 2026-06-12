---
title: "S3 Wide Resolution?"
date: 2007-05-19
forum: General Help
---

### Post by LAurel on 2007-05-19
Hello, everyone,

I'd like to know if I can use my monitor's (LG 204WT) native resolution of 1680x1050 on an S3 integrated graphics chip (xorg recognizes it as S3 Inc. VT8375 [ProSavage 8 KM266/KL266]).

I have my resolution in the xorg.conf file, but it doesn't show up when actually trying to set my screen resolution.

I've read on the wiki that for Intel graphics I can override the video bios using an application that can force the chip to deliver a correct resolution, even if it is not normally supported. I'd like to know if anyone can point me to a similar solution for the S3 chip.

Thanks!

---

### Post by Psicolonia on 2007-05-19
try this, it worked for me several times: go to xorg.conf and erase all other resolutions. leave that one only.

OH BACK IT UP BEFORE DOING IT!!!

:) tell me how it went.

---

### Post by LAurel on 2007-05-19
Thank you for the reply, Psicolonia, but it sadly doesn't work. After editing xorg.conf and rebooting, my resolution is still the 1280x1024 I had before, and when trying to set a new resolution, I get to choose from 640x480, 800x600, 1024x768 and 1280x1024. Something is wrong here :( .

---

### Post by Psicolonia on 2007-05-19
:( sorry... don't know what to do next... can you set up a wide screen with the same proportion? like 1280x768? by forcing it on xorg.conf??

---

