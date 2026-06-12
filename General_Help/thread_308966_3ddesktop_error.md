---
title: "3ddesktop error"
date: 2006-11-28
forum: General Help
---

### Post by xenoalien on 2006-11-28
I get an error when I try to run 3ddesktop:


xenoalien@xenoalien:~$ 3ddesk
Attempting to start 3ddesktop server.
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Daemon started.  Run 3ddesk to activate.
Server not found after waiting 5 seconds.
Could not find server.
Try starting manually (3ddeskd)


Anyone know what this means? And how can I fix it?

Thanks

---

### Post by syrleb on 2006-11-28
hey, i dont get an error, but mine only shows one of my desktops until it opens it, its the worst program on earth dont bother

---

### Post by xenoalien on 2006-11-28
Alright, is there a program like 3ddesktop worth using?

---

### Post by syrleb on 2006-11-28
get XGL and compiz, it looks much better, and it not only changes desktops in 3d, it makes everything look better. search XGL on google and see for yourself, i would have gave you a link but i lost it sorry

---

### Post by DarkN00b on 2006-11-29
**xenoalien:**

It looks like you don't have direct rendering enabled on your system. Could we have a look at your /etc/x11/xorg.conf? Also, what video card do you have?

**syrleb:**

Try running this in a terminal first:
```
3ddesk --acquire
```

Then run 3ddesk.

---

### Post by syrleb on 2006-11-29
thanks, but i already tried that, i tried everything, i dont know whats wrong with it, and dont really care xgl looks way better

---

### Post by ithuwakaga on 2007-04-20
Try updating your drivers.  I had this exact same problem, but didn't realize that I had accidentally disabled them.  I randomly reinstalled them and it works.

Maybe that happened.

---

