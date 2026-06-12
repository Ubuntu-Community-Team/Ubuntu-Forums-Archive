---
title: "3DDesktop Error"
date: 2006-10-10
forum: General Help
---

### Post by Old Pink on 2006-10-10
> matt@matt-desktop:~$ 3ddesk
Attempting to start 3ddesktop server.
Daemon started.  Run 3ddesk to activate.
3ddeskd: glXIsDirect failed, no Direct Rendering possible!
3ddeskd: Please configure hardware acceleration.  Exiting.
Server not found after waiting 5 seconds.
Could not find server.
Try starting manually (3ddeskd)

matt@matt-desktop:~$ 3ddeskd
Daemon started.  Run 3ddesk to activate.
matt@matt-desktop:~$ 3ddeskd: glXIsDirect failed, no Direct Rendering possible!
3ddeskd: Please configure hardware acceleration.  Exiting.

Any ideas? :) Can't seem to get past this error....

---

### Post by mssever on 2006-10-10
I get that occasionally and logging out and back in fixes it. I believe it's related to video drivers.

---

### Post by Old Pink on 2006-10-10
Hm, no luck there for me! :(

---

### Post by PriceChild on 2006-10-10
You have installed proper video drivers?

```
glxinfo
```
The third line or so MUST say:
```
direct rendering: Yes
```
If not then simply post your video card and we can get you a link to how to install the necessary drivers :)

---

### Post by Old Pink on 2006-10-11
I get:```
direct rendering: No
```... mind helping me get my drivers installed then? :)

How do I know which card I'm using? My device manager broke when gtkpod 0.99.8 got it's dependencies... (that stupid application fucks everthing up)

**EDIT: **SiS 962 is my card, thanks. :D
The SiS website is pretty unclear, but says there aren't any linux drivers for 962, and the default ones are included in most distros?

---

### Post by Old Pink on 2006-10-11
Changed my driver from wacom to sis... did **not** go well, had to restore xorg.conf from terminal. ;)

---

### Post by Old Pink on 2006-10-15
I hate to nag, but 4 days and no reply? :(

---

### Post by skyshock21 on 2006-10-15
> **Matt.H said:**
> I hate to nag, but 4 days and no reply? :(

You might consider posting this in the Sound and Video forum.  You might get more responses there.  ;)

---

### Post by Thinker NO. 1 on 2006-11-07
I have got the same problem like Old Pink. I stuck at this
```

direct rendering: No
```

---

