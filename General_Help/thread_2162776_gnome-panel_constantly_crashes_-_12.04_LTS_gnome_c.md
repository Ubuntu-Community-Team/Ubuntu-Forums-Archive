---
title: "gnome-panel constantly crashes - 12.04 LTS gnome classic"
date: 2013-07-15
forum: General Help
---

### Post by conmat on 2013-07-15
I just installed 12.04.02 LTS 64-bit on a Lenovo T400 laptop.  I've been running 10.04 LTS on this system with no problems but the repositories are gone so I have to switch to 12.04  I don't like Unity so I installed gnome following these instructions:
[http://blogs.operationaldynamics.com/paul/opensource/not-unified-removing-unity-from-ubuntu-12-04-lts](http://blogs.operationaldynamics.com/paul/opensource/not-unified-removing-unity-from-ubuntu-12-04-lts)
which is about the same as this:
[http://ubuntuforums.org/showthread.php?t=1966370](http://ubuntuforums.org/showthread.php?t=1966370)


I like the "top" panel (with the clock) to be on the left and the "bottom" panel to be on the right.  When I move both panels gnome-panel crashes and gives this error:
```
(gnome-panel:2430): Gtk-WARNING **: drawing failure for widget `GtkToggleButton': invalid matrix (not invertible)

(gnome-panel:2430): Gtk-WARNING **: drawing failure for widget `WnckTasklist': invalid matrix (not invertible)

(gnome-panel:2430): Gtk-WARNING **: drawing failure for widget `PanelApplet': invalid matrix (not invertible)

(gnome-panel:2430): Gtk-WARNING **: drawing failure for widget `GtkToggleButton': invalid matrix (not invertible)

(gnome-panel:2430): Gtk-WARNING **: drawing failure for widget `WnckTasklist': invalid matrix (not invertible)

(gnome-panel:2430): Gtk-WARNING **: drawing failure for widget `PanelApplet': invalid matrix (not invertible)

(gnome-panel:2430): Gtk-WARNING **: drawing failure for widget `GtkToggleButton': invalid matrix (not invertible)

(gnome-panel:2430): Gtk-WARNING **: drawing failure for widget `WnckTasklist': invalid matrix (not invertible)

(gnome-panel:2430): Gtk-WARNING **: drawing failure for widget `PanelApplet': invalid matrix (not invertible)

(gnome-panel:2430): Gtk-WARNING **: drawing failure for widget `GtkToggleButton': invalid matrix (not invertible)

(gnome-panel:2430): Gtk-WARNING **: drawing failure for widget `WnckTasklist': invalid matrix (not invertible)

(gnome-panel:2430): Gtk-WARNING **: drawing failure for widget `PanelApplet': invalid matrix (not invertible)
```
AND
```
Floating point exception (core dumped)
```
If an application is minimized it does not show up on the right side panel.

Is there any way to fix this?
I would like my environment to look just like 10.04 LTS

Thanks

---

### Post by hansdown on 2013-07-15
Hi conmat.

I loved 10.04. It was my  most liked version.

This line

> gnome-panel:2430): Gtk-WARNING **: drawing failure for widget `GtkToggleButton': invalid matrix (not invertible)

Leads to this...

[http://bugs.solusos.com/index.php?do=details&task_id=10](http://bugs.solusos.com/index.php?do=details&task_id=10)





> Floating point exception (core dumped)

leads to this....

You are getting the error "Floating Point Error ( Core Dump )".

This error comes when there is some expression dividing value by zero. eg. x=10 and y=0 and x/y. This means, x is divided by zero, which results to floating point error.

Please check is your code doing division by zero? Try to resolve this zero value before expression evaluation. And thats it. Your problem is solved.

I was facing the same error which got resolved by checking variable values not equal to zero before expression evaluation.

I wish people facing this error gets solution, hence writing this report.

I'm not trying to be a smart-guy, but 10.04, no matter how much we liked them, are no longer attainable.

---

### Post by conmat on 2013-07-16
Hello, thank you for your reply.

All the errors are from gnome panel-crashing.  I wish it was my code so I could fix it!

I deleted the clock but gnome-panel still crashes and minimized applications do not appear in the panel.

If I keep one panel on the bottom of the screen gnome-panel does not crash but this is an annoying work-around.

It looks like someone is working on fixing the clock app.  Do you think this will fix these problems?

I would like your suggestion:
Keep working on 12.04 LTS?
Install UbuntuGNOME 13.04?
Install Xbuntu?
Install MINT with MATE?

I would like a LTS release but it seems 12.04 is very buggy.

Thanks

P.S.  I think 10.04 LTS was an evil plot to get people hooked on Ubuntu so then the developers could change everything and make the rest of us suffer!

---

### Post by conmat on 2013-07-16
Also found this bug report:

[https://bugzilla.gnome.org/show_bug.cgi?id=94625#c737](https://bugzilla.gnome.org/show_bug.cgi?id=94625#c737)

11 years old :-o

[URL="https://bugzilla.gnome.org/show_bug.cgi?id=94625#c737"]
[/URL]

---

### Post by hansdown on 2013-07-16
xubuntu 13.04 is nice.

I also use mint cinnamon 15.

Both have top and bottom panels, and can be customized.

---

