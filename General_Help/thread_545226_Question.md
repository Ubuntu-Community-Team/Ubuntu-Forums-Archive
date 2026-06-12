---
title: "Question"
date: 2007-09-07
forum: General Help
---

### Post by Dracar on 2007-09-07
I was working on my screen resolution because it was 800x600 and i wanted it to be 1280x800. I entered this
```

sudo dpkg -reconfigure -phigh xserver -xorg

```
After i ran that it prompted me for a graphics card model and i just hit enter, now its running in terminal mode and i cannot figure out how to fix it, any help?

---

### Post by merlinus on 2007-09-07
Run the command again, and for now, select vesa for your video driver.

-merlin

---

### Post by Dracar on 2007-09-07
ok, how do i safely restart from this? i tried shutdown 1 but it just switched to single user mode, oh and also, it makes a backup each time so i assume there is a way i can just rename the original backup, then replace the xorg.conf file with it if this doesn't work.

---

### Post by merlinus on 2007-09-07
**startx** should get you to a gui, if it works.

And yes, backups of /etc/X11/xorg.conf are made automatically, so you might be able to go back and find the one that was working before you tried to change the screen resolutions.

Gutsy will have a gui for changing x-server settings, but there is one you can install for use with ubuntu. 

[http://www.cyskat.de/dee/progxorg.htm](http://www.cyskat.de/dee/progxorg.htm)

-merlin

---

### Post by Dracar on 2007-09-07
Ok, i have it back to normal, il just have to live with the 800x600 lol. Thanks for your help again.

---

### Post by merlinus on 2007-09-07
Glad it is working, but you might try the x-server configuration gui to get a better screen resolution.

Just remember which xorg.conf backup file will get you back to where you started!

-merlin

---

