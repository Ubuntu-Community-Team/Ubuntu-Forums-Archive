---
title: "Main monitor artifacting very badly, believe it is due to a startup script"
date: 2016-08-12
forum: General Help
---

### Post by shyshy2 on 2016-08-12
I believe that a startup application is causing my main monitor to artifact and basically be unusuable, due to a start up application that I cannot find.

The reason I believe this is because I have a set of steps that I can confidently reproduce this problem with.

I have a separate /home partition from another Ubuntu install, which I very clearly remember adding some sort of start up script that ran pkill to fix a display framerate issue. Whenever I go through the process of remounting this /home directory, on restart, the artifacting immediately reappears. I cannot find the script under Startup Applications.

I do remember this causing an issue on the previous Ubuntu install, but, it manifested itself in a different way and I think it was due to me using the Gnome desktop, but currently on a fresh install with Unity, it's completely hosed.

---

### Post by shyshy2 on 2016-08-12
Hah, solved it actually. If anyone's curious, it was due to a change made inside ~/.config/monitors.xml that I had made in the old partition. I had set it to 144hz, but turning it back down to 60hz fixed it.

---

