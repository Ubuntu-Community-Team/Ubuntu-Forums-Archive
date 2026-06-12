---
title: "Problems with selecting Mplayer as the default player for videos"
date: 2005-09-27
forum: General Help
---

### Post by feloc on 2005-09-27
I try to put Mplayer as a default player for videos. When I play the video (.mpg) in terminal mplayer (and the video) works just fine. I had Totem as a default .mpg player before, I removed it recently and now got this problem. What to do?

Double-clicking the file gives:
The filename "video.mpg" indicates that this file is of type "MPEG video". The contents of the file indicate that the file is of type "

Right-Click -> Properties -> Open With -> Mplayer
= Could not add application to the application database.

Right-Click -> Open with other application -> Mplayer
= Could not add application to the application database.

When I try to do the same thing with VLC, I get the same error...

What to do?

---

### Post by Perfect Storm on 2005-09-27
VLC:

<right click file> ---> <open with> ---> <Use a custom command> and write wxvlc

Now <properties> ---> <Open with> ---> choose wxvlc

---

