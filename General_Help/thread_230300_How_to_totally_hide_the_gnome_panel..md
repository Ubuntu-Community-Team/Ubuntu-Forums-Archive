---
title: "How to totally hide the gnome panel."
date: 2006-08-05
forum: General Help
---

### Post by GAZ082 on 2006-08-05
Yes. I goggled for it, seached within these forums, but i can't get a solution. I already edited with the gconf-editor tool the minimum pixels thingie but no help. I wannta totally hide the damn bar!

---

### Post by nickleus on 2007-02-28
i agree, this is completely ridiculous. kde manages it fine so why can't gnome?

---

### Post by anaconda on 2007-02-28
how about going to panel properties and check the "show hide buttons" tab.. then when you click on the hide button the panel disappears..

I dont mind that the autohide leaves few pixels showing.. but I understand it can be annoying..

---

### Post by Quillz on 2007-02-28
> **nickleus said:**
> i agree, this is completely ridiculous. kde manages it fine so why can't gnome?
KDE is a completely different window manager. Just because KDE can do something doesn't mean GNOME has to do it the same way, as well.

That said, I don't know if the GNOME panel can be disabled, since it generally wants you to use the system tray for applets and other info.

---

### Post by mcduck on 2007-02-28
You can change the minimize size to 1 pixel in gconf-editor, but it's not possible to make it completely hidden. Gnome-panel is coded so that it unhides when you move the mouse cursor over the panel, so it needs at least that 1-pixel wide area so you can unhide it.

I think the 1 pixel wide minimized panel is OK, if you don't know it's there you won't even notice it.

For those who don't know how to do this:

1. hit Alt-F2 and run 'gconf-editor'
2. browse to apps/panel/toplevels/<your panel name here>
3. change 'auto_hide_size' to 1
(4. while you are there, you can also change hide_delay & unhide_delay to your liking. the values are in milliseconds, so '500' means 1/2 of a second.)

---

### Post by nickleus on 2007-02-28
>if you don't know it's there you won't even notice it.
are you kidding? you're the one who actively chose to hide it. you KNOW its there. and you can make it appear by using the keyboard shortcut alt+f1 if you want to show it.

when you play hide and seek, you hide completely and the other person seeks you. it's not called "hide-except-for-1-pixel and seek"...

i maintain that this is one of the dumbest things about gnome. i switched to kde PRIMARILY because of this..

---

### Post by zvacet on 2007-02-28
If it is so much trouble to you,why don´t you delete it?Right click on the panel and choose delete.Problem solved.

---

### Post by m.e.danko on 2007-02-28
> **zvacet said:**
> If it is so much trouble to you,why don´t you delete it?Right click on the panel and choose delete.Problem solved.

You can't delete the last panel, when you right click on the last panel the "Delete This Panel" menu item is grayed out.

---

### Post by mcduck on 2007-02-28
Just remove 'gnome-panel' from your session in System/Preferences/Session/Current Session and then you should be able to 'killall gnome-panel' to get rid of the panels completely :)

---

### Post by strabes on 2007-02-28
If you don't want a panel just use a window manager other than metacity

---

### Post by llamakc on 2007-02-28
Metacity doesn't handle the panels, it manages windows and handles window decorations.

---

### Post by nkataria on 2007-06-08
You can totally hide Gnome Panel. Follow the procedure below::
1. In Terminal, give "gnome-session-properties" command.
2. Choose "Current Session" tab.
3. Click on "gnome-panel" and click remove.
4. Apply and close.
5. In terminal give "gnome-session-save".
You are done. gnome-panel will not bug you again:popcorn:

---

### Post by nickleus on 2007-06-08
that's not hiding it, that's deleting it. i want to completely hide it, but when i press "alt+f1" i want it to appear again...kde does this fine...but thanks for the tip on how to delete it. cool that that is possible now =)

---

### Post by WestCoastSuccess on 2007-06-15
Many, many thanks McDuck for the 1 pixel solution - it's been driving me nuts having 6 pixels at the top of the screen in Mythtv - one less thing to stress about!

---

### Post by H_out on 2007-08-18
If you still hate seeing the 1-pixel, you can also set the panel to be completely transparent.

Here's something else you can try:  if you go into gconf-editor and play with the "monitor" or "screen" values, you can get gnome-panel to bug out.  I've played with it a little by changing the values to various numbers (0 to 4).  With certain "screen" values it caused my system to run sluggish.  With a different "monitor" setting I got the panel to completely disappear without any other ill effects.

Personally, I think it's useful to still have gnome-panel running at the bottom while the panel is still (virtually) invisible.  This way, I can still press Alt-F1 if I need to get to something I don't have access to in my dock.

---

