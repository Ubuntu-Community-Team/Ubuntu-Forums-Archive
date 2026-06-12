---
title: "Looking for an icon theme with massively sized icons..."
date: 2014-10-10
forum: General Help
---

### Post by Roasted on 2014-10-10
Hello friends. I'm working on a project at work (school district) with a student who will be utilizing an Ubuntu system to assist with their visual difficulties. The only catch is the icons are way too small. Icons such as New, Open, Save, etc in various applications.

Is there a way to scale these up globally? Or does a theme exist somewhere that has huge icons?

All I can find when I search are older posts of people asking how to downsize the icons, such as in the Unity launcher back when 32px was the minimum, etc. Anybody have any idea?

EDIT - The primary use of this system will be through an application called Xournal, which will allow the student to bring up scanned PDF worksheets, draw on them via the touch screen to put in answers, and export the new document as PDF. This file would get auto-transferred via ownCloud back to the teacher for grading with a shared folder. I asked on the Xournal mailing list to see if I could get some more info. In the mean time, I manually scaled up all of the Xournal specific icons. This was the result:

[http://oi62.tinypic.com/1z35oci.jpg](http://oi62.tinypic.com/1z35oci.jpg)

Clearly you can see that this worked for Xournal specific icons, but not system wide icons, such as the Save, New, and Open buttons in the top row. These icons are drawn from the system theme. 

A response back from the mailing list (very quickly, might I add) provided an idea. I changed a line in my /usr/share/themes/Radiance/gtk-2.0/gtkrc file, from:

```
gtk-icon-sizes = "panel-menu=22,22:gtk-button=16,16"
```
to
```
gtk-icon-sizes = "panel-menu=64,64:panel=64,64:gtk-menu=64,64:gtk-large-toolbar=64,64:gtk-small-toolbar=64,64:gtk-button=64,64"
```

This resulted in something much better, i.e.:

[http://oi60.tinypic.com/bjevfb.jpg](http://oi60.tinypic.com/bjevfb.jpg)

Now mind you, this is GREAT. Xournal will be the very most primary use of this system. That said, Ubuntu 14.04 provides a lot of additional usability features, from simple things that have been around for a long time like the ability to increase font size, to the relatively new feature of display scaling (System Settings >> Displays >> Scaling). All of these things combined are a true win.

Now here's where I get really curious... I made a change in the gtk-2.0/gtkrc file. How would I accomplish the same thing if I were in a full GTK3 environment? What if Ubuntu was 100% Qt today? How would I make this change on a Qt platform?

While I have the answer I need right now, today, I'm still curious how I would accomplish the same task but on a different type of setup, i.e. GTK3 or Qt. Anybody have any ideas?

---

