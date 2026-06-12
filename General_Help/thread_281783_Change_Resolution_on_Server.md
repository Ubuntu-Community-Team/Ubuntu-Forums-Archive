---
title: "Change Resolution on Server"
date: 2006-10-21
forum: General Help
---

### Post by wayne on 2006-10-21
I installed Ubuntu server and having a problem with seeing the text on the left side of the monitor.  I have tried adjusting the horizontal position with the monitor controls, but I still cannot see about 5 characters. Is there a way to change the resolution so I can view all the text?  To be clear this is in the command line mode not a GUI interface.

Thanks
Wayne

---

### Post by CatKiller on 2006-10-21
I've noticed that installing the nVidia driver for my nVidia card caused the monitor to re-centre the display on the monitor. I was also looking at the documentation on the nVidia site the other day (don't ask :roll:) and noticed that there are xorg.conf options to fiddle with the position on the monitor. Can't remember exactly what they were now.

So you could try installing a different driver for your graphics card, even though you're only using the console, and you could examine the documentation for whichever driver you're using to see if that driver has a similar option for adjusting the display position.

---

