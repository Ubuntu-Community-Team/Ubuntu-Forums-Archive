---
title: "Gutsy screen resolution problem...help!"
date: 2007-09-07
forum: General Help
---

### Post by seaborn on 2007-09-07
Hi,

   I installed Gutsy tribe 5 yesterday afternoon - I was really enjoying it, and everything was working fine... I had just configured wireless and compiz when I figured that it was a good time to reboot my notebook.

   Upon reboot, everything was going as usual. I got to the login screen in my standard 1024 resolution, but as soon as I had finished entering my password and started the actual login process, my screen resolution was changed without warning to 640. I'm on an intel X3100 for graphics if that makes any difference, and I know that I have it configured properly because I had the compiz desktop effects working with it before this happened (in 1024 resolution).

   Every time I go to change the resolution up to 1024 again in my preferences, or even up to 800 for that matter, the resolution changes, but then the actual screen area shrinks smaller into the upper left corner, and gets surrounded by black screen space to the right and to the bottom.

   It is really annoying trying to work in 640 resolution....I would really appreciate any help you could give me!

Thanks,
Geoff

---

### Post by jnorthr on 2007-09-07
Just to clarify this one - your login screen looks to be 1024 but when you are given the ubuntu desktop it becomes 640x480-ish ? What does system>preferences>screen resolution show ? Have you done an update from tribe 4, if so did it seem to work ok there ?

---

### Post by seaborn on 2007-09-07
Hi, yes my login screen looks like 1024, but when I'm in the desktop it switches to 640. My system>preferences>screen resolution shows 640, but when I switch it to 1024 I get the problem I described above. I did the install directly on Tribe 5, I never tried it on Tribe 4.

---

### Post by boteeka on 2007-10-12
I have the same problem, but with different parameters.

My login screen (GDM) is at a resolution 1280x1024, but the viewable area is something like 1024x768 (smaller than the previous). This leads to a strange effect that I can "scroll" the login screen with the mouse touching the screen edges. It gives a feeling that the login screen doesn't fit into the viewable are.

I think if the login screen's resolution is actually lower than the screen's resolution than the black right and bottom edges show up, as the login screen doesn't cover all the viewable area for some people here in the forums.  

It should be fixed in a way that GDM (or KDM or whatever is used) should show up at the same resolution as the desktop was set.

---

