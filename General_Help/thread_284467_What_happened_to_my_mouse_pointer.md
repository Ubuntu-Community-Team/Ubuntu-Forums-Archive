---
title: "What happened to my mouse pointer?"
date: 2006-10-25
forum: General Help
---

### Post by namelessone on 2006-10-25
I used the application gcursor to change my default mouse pointer to a much better looking one I found on gnome-look.org.

The only problem is, whenever I use wine--or I should say, when I'm done using wine, my cursor is shaped like it was before, but it is all black and kinda fuzzy looking. The cursor always looks like this until I restart the computer.

Does anybody know how to fix this?

---

### Post by Yopo on 2007-01-02
I have the same problem.
After any program I load that works with wine my cursor turns black. But it has nothing to do with the change you did to the cursor you've got from gnome-look. Because I use the default one from Ubuntu and like I said, it also happens to me.

I guess there are more people who have the same problem, are there?

And offcourse i also like to know if someone knows a solution for it...

---

### Post by julep on 2007-07-08
Me too. I don't use wine either but my cursor turns black every time the desktop comes back from the screen saver. I'm using a new and very vanilla xubuntu install. It doesn't have anything to do with wine and it's rather annoying.

---

### Post by winger1312 on 2007-07-13
I have the same problem.  Mine occurs whenever my pointer needs to click over a pic, chat line, or oprogram.  very odd

---

### Post by nautical9 on 2007-09-27
No guarantees, but try editing your /etc/X11/xorg.conf file, and add the following lines within the Section "Device" area for your graphics card:
```
Option "SWCursor"
```

If your card is an ATI Rage 128 or similar, try this right next to the above line:
```
Option "ForcePCIMode" "true"
```

---

