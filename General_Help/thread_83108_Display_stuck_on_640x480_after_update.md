---
title: "Display stuck on 640x480 after update"
date: 2005-10-27
forum: General Help
---

### Post by cayblood on 2005-10-27
I installed ubuntu 5.10 on my Dell Latitude D610 (w/ onboard Intel graphics card--can't remember offhand the exact model).  Everything worked spendidly.

However, upon logging in, I was informed that some updates were available.  After installing all the updates, my display is stuck on 640x480 and none of the previous resolutions are available.  Anybody have any ideas as to what might be wrong?  I could start delving into the X configuration but I'm thinking somebody probably has seen this before and could tell me right away.

Thanks,

Carl Youngblood

---

### Post by Remmelas on 2005-10-27
[QUOTE=cayblood]I installed ubuntu 5.10 on my Dell Latitude D610 (w/ onboard Intel graphics card--can't remember offhand the exact model).  Everything worked spendidly.

However, upon logging in, I was informed that some updates were available.  After installing all the updates, my display is stuck on 640x480 and none of the previous resolutions are available.  Anybody have any ideas as to what might be wrong?  I could start delving into the X configuration but I'm thinking somebody probably has seen this before and could tell me right away.

Thanks,

Carl Youngblood[/QUOTE]

I'm afraid i've not seen it, but reconfiguring X is fairly trivial, sudo dpkg-reconfigure xserver-xorg and answer the questions.  Before doing that, maybe peek inside xorg.conf and see if for some reason the display section only contains the 640x480 resolution

---

### Post by Breaks on 2005-10-27
Well, as stupid as it sounds, have you tried a restart? when i was using hoary on a dell dimension i had this issue after updating, but when i restarted all was well and my res was back to normal believe it or not.... 

If this doesnt work then yes you will most likely have to edit your xconf.

---

### Post by Qrk on 2005-10-27
sudo dpkg-reconfigure xserver-xorg

Change nv to vesa. Its one of the first options. (Most often this is the case, you might have a different problem though)

---

