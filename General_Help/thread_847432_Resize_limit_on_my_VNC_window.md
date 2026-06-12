---
title: "Resize limit on my VNC window"
date: 2008-07-02
forum: General Help
---

### Post by ajcrm125 on 2008-07-02
I have a rather large display.  I jump onto a machine and create a vncserver with 1300x800 geometry.  When I open up Vncviewer on my Ubuntu box it displays properly but with scroll bars. I try to drag and resize the window and it will enlarge to a point but then stop.  Almost like there a limit defining how large I can resize th window.  

My screen is 1280x1024 so I should at least be able to make the window tall enough so I don't see the vertical scroll bar anymore.

Any idea what's setting the limit on this window such that I can't resize it as much a possible?

Thanks,

---

### Post by prince_niceguy on 2008-07-02
i have found the ts client with gnome not do scaling which is kind of annoying. what you can do is install krdc and then connect to your vncbox and click on scale. That should scale your windows.

---

### Post by ajcrm125 on 2008-07-03
Found the problem.  Turns out that if the vnc display will not fit within the X dimension of your screen the it will place the scrollbars regardless.  So I had to fine tune the geometry in the X dimension to get it to fit first and then the Y.

---

