---
title: "Windows will open in a corner of the screen"
date: 2015-03-05
forum: General Help
---

### Post by chavoush.k on 2015-03-05
So every time I open files, the window is snapped to the lower right corner. When I open my USB drive, it's snapped to the upper left corner. Terminal is also snapped to the upper left. Most of the other apps open centered. It's not the biggest issue, but still quite annoying, so anything I can do about this? I would like all applications to open centered.

Edit: the corner in which apps open change randomly

---

### Post by deadflowr on 2015-03-05
The way apps open like that is called Smart.
Smart is designed to open new windows without overlapping existing windows.
To change it, you can install a program called compizconfig-settings-manager(it is in the software center)
In this program go to the section marked Place Windows.
Click on the line for Placement Mode and select which ever option you would like.(And yes, Centered is an option)

Compiz is the default window manager program used by Ubuntu, and compizconfig-settings-manager, as you might guess, is a control panel of sorts to adjust compiz to your liking.

Caveats to using ccsm(compizconfig-settings-manager- shortname) are that it is very powerful and unless you are sure about what you are doing within it, try to minimize your usage of it.
One of the programs biggest hassles, if you will, is that when you make changes it can/will readjust itself. These readjusts are akin to a reload, or reset so when they happen they may cause the system to act odd, if only for a minute or so.
When these adjusts take place, do not do anything. While it may seem like the system has broken, ie, the screen completely freezes, it is in fact resetting itself. Under these circumstances it is best to let it play out, and do not, I cannot stress this enough, do not try to shutdown the machine. A machine shutdown might leave the machine in a totally broken set, which in most cases would have been completely fine if left alone.

But that is not to say there aren't plenty of changes you can make to it.
If you have questions about whether or not, and how, you can adjust various settings, do not hesitate to ask here, in these forums.

Hope this helps.

---

### Post by CantankRus on 2015-03-05
You can also change the compiz placement mode setting to centered via terminal....
```
dconf write /org/compiz/profiles/unity/plugins/place/mode 1
```

---

