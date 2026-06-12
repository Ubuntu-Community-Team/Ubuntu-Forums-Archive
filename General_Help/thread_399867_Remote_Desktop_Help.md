---
title: "Remote Desktop Help"
date: 2007-04-02
forum: General Help
---

### Post by joebu23 on 2007-04-02
Hello, I need to VNC from a windows computer (VNC is the only option) to an ubuntu box.  The ubuntu box in question is running two video cards with twinview on each one, thus the display is 4 monitors wide.  I need to be able to VNC into the computer to administrate it but when I currently vnc into the computer, I can only get to the output from the main card.  


Any ideas, suggestions?

---

### Post by bradleyd on 2007-04-02
what vnc server are you using on Linux side?

---

### Post by joebu23 on 2007-04-02
using vino-server.  is there something better?

---

### Post by bradleyd on 2007-04-02
if you are running Xinerama you should try x11vnc. Karl has done a great job.
look here for more info [http://www.karlrunge.com/x11vnc/](http://www.karlrunge.com/x11vnc/)

---

### Post by joebu23 on 2007-04-02
Xinerama would be great, but that opens a whole new mess of problems.

1. you cannot open a terminal in xinerama.  It is some bug that is known

2. If i try to play video in xinerama (which is what this machine is for) the other video card displays black instead of the video and I cannot find anything to correct this.

---

### Post by bradleyd on 2007-04-02
you can then run multile instances of x11vnc, not the best but will work.

---

### Post by joebu23 on 2007-04-02
I'll take a look, thanks

---

### Post by joebu23 on 2007-04-02
It works great, but afterward, it seemed as though the server had made the ctl key sticky.  do you know a fix for this?

---

