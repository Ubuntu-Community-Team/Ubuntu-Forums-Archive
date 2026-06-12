---
title: "Adding text to the panel"
date: 2008-06-22
forum: General Help
---

### Post by change_mode on 2008-06-22
Hey
I simply want to add custom text to the system panel, but I can't figure out how.
The reason is that I want it to read "CPU" and "memory" in front of the system load indicator to make it look better.

What's the best way to do this?

---

### Post by konerx on 2008-12-16
I'm also curious how to do this. I want to add some text that says what task I'm currently working on. It's easy to get side-tracked. :P

---

### Post by drs305 on 2008-12-16
This will certainly not qualify as the 'best' solution. You can make an icon with gimp or any other graphics program. With my resolution I use a 40x40 pixel size. Insert your text, make the background transparent if you wish, then make a custom launcher, add your custom icon, and add it to the panel. You will have to include either a real or dummy command.

---

### Post by konerx on 2008-12-16
That was the first thing I thought of. I then started looking into how to make an applet from scratch that would just display some text, since I'm pretty sure applets are able to display whatever text they want (e.g. the Time/Date applet). I couldn't find anything about how to write an applet, though.

---

### Post by konerx on 2008-12-18
Here's an even hackier hack. I got the idea from [Tips4Linux]("http://tips4linux.com/custom-clock-in-gnome/") (via [Lifehacker]("http://lifehacker.com/5113092/customize-your-linux-panel-clock")).

Basically, I added a new Clock applet to the panel, opened gconf-editor, and found the duplicate applet preferences at apps/panel/applets/**applet_6**/prefs (my original clock was stored at clock_screen0).

I changed the *format* field to "custom", and was then able to add whatever text I wanted to the *custom_format* field.

Tada! I now have a custom label on the panel.

---

### Post by drs305 on 2008-12-18
konerx,

Very nice! Definitely a keeper.

---

