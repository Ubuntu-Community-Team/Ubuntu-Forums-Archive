---
title: "launcher sticky"
date: 2012-11-04
forum: General Help
---

### Post by Kevin McCready on 2012-11-04
Here is another case for a sticky, or a pointer to stickies. 

In trying to solve my problem I've seen hundreds of threads. Lots of people have all sorts of problems with launchers and I think a sticky might help.

Anyway, here's my problem. I simply want to be able to launch an app from the taskbar. How do I put the app's icon on the taskbar? I tried dragging and dropping but it didn't work.

---

### Post by MG&amp;TL on 2012-11-04
Maybe...wiki page instead?

As your thread is tagged Lubuntu, I'll assume you mean lxpanel, Lubuntu's default panel. In which case, no, drag'n'drop doesn't work. You have to right-click on the existing application launcher (or add one to the panel), and select settings :).

---

### Post by Kevin McCready on 2012-11-04
Sorry, I should have said I already tried that. When you right click on the panel and choose either "Panel Settings" or "Add /Remove Panel Items" you got a dialogue box with 4 tabs (Geometry, Appearance, Panel Applets, Advanced). I can't see anywhere in any of the tabs how to add an app of my choice.

---

### Post by ajgreeny on 2012-11-04
One of the panel applets you can add is "Application launcher" so do that first, then you can add an application to that.  It is simple, but has to be done in the two stages.

---

### Post by Kevin McCready on 2012-11-04
> **ajgreeny said:**
> One of the panel applets you can add is "Application launcher" so do that first, then you can add an application to that.  It is simple, but has to be done in the two stages.

Thanks. After a bit of mucking around I found
1. click the "application launch bar" applet
2. click edit
3. another window pops up BEHIND the active window.
4. move the active window out of the way
5.  find the application you want 
6. click add

hmmm. got there in the end BUT
Now the icon is on the bottom right side of the window, even further right than the time display. Is there are way to bring it back to the left side near the menu icon?

---

### Post by vasa1 on 2012-11-04
> **Kevin McCready said:**
> ...
Now the icon is on the bottom right side of the window, even further right than the time display. Is there are way to bring it back to the left side near the menu icon?
Yes. You can use the **up** and **down** arrows to reposition icons **horizontally**. But, AFAIK, some of them move as a block (the indicator applet set?).

---

### Post by Kevin McCready on 2012-11-04
Cool. Thanks. The arrows in the panel applet dialogue box did the trick (I selected the launch application one). The only problem is that if you have more than one "launch application" applet, you have to know which one relates to which icon.

---

### Post by ajgreeny on 2012-11-05
> **Kevin McCready said:**
> Cool. Thanks. The arrows in the panel applet dialogue box did the trick (I selected the launch application one). The only problem is that if you have more than one "launch application" applet, you have to know which one relates to which icon.
From the list of applets you see installed already when you open the "Add Panel Applet" dialog, you simply need to count from side to side of your panel and you can quickly work out which is which.  There is always one Application Launcher applet on the far right of the default panel, if I remember correctly, which contains the "shutdown" icon.

---

### Post by Kevin McCready on 2012-11-08
hmmm. thanks. computers count better than me. I managed to delete the shutdown one. I'll try to get it back.

---

### Post by ajgreeny on 2012-11-09
Open the file **.config/lxpanel/Lubuntu/panels/panel** in leafpad and add 
```
Plugin {
    type = launchbar
    Config {
        Button {
            id=/usr/share/applications/synaptic.desktop
        }
        Button {
            id=lubuntu-logout.desktop
        }
    }
}
```
to the bottom and it should add back in the shutdown icon and synaptic, which is just my preference; remove synaptic if you don't want that as well.

I also removed the shutdown button once by mistake, and then took a long time to figure out how to get it back.

---

