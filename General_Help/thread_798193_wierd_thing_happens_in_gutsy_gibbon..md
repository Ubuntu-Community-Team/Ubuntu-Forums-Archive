---
title: "wierd thing happens in gutsy gibbon."
date: 2008-05-18
forum: General Help
---

### Post by 84loops on 2008-05-18
I just installed today. I had a lot of trouble before but now I think it's runs ok. Everything is fine. I even have basic desktop effects when xorg.conf lists a generic monitor. When I select detect and ubuntu finds my actual monitor all desktop effects go away and xorg.conf lists nv instead of nvidia as the driver. How can I it set so my actual monitor is selected and the nvidia driver selected while using desktop effects? I hope this is clear.

---

### Post by empthollow on 2008-05-18
when you select detect, it sounds like ubuntu is detecting the monitor and video card drivers.  if you tell it to detect your monitor and manually edit the /etc/X11/xorg.conf file and change nv to nvidia, you should be all set next reboot.

---

### Post by 84loops on 2008-05-18
yea I tried that. Still didn't work right. I just removed the desktop effects anyways, slows down the system a little bit. I am using onboard GPU. So that's probably why it doesn't work to well. Any thing else I can try?

---

### Post by empthollow on 2008-05-18
I'm not sure what else to suggest, i use the generic 1280x1024 monitor setting on my system because i know that's the resolution my monitor supports and i don't have a listed driver.

---

### Post by 84loops on 2008-05-19
It actually works now, well for now.

---

### Post by empthollow on 2008-05-19
that's good, if it ain't broke, don't fix it:popcorn:

---

