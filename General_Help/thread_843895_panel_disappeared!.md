---
title: "panel disappeared!"
date: 2008-06-28
forum: General Help
---

### Post by Phyrax on 2008-06-28
i installed awn, and i'm a n00b and so i didn't want the panel anymore to hold my windows. so i right clicked and said "remove panel" but now it's got some weird graphic and it's not completely gone, i can't right click on this weird graphic (it changes the graphic to whatever is moved over the space)

how do i either

a- get rid of the graphic

or

b- get my panel back


any help would be great thanks!

---

### Post by dizee on 2008-06-28
try ```
killall gnome-panel
```

it should restart. if not press Alt+F2 and run ```
gnome-panel
```

---

### Post by Phyrax on 2008-06-28
it's not the top panel it's the one at the bottom, so it seems to restart if i do that, but the other panel (the bottom one) is still there.

i also tried to end the process, but that didn't work.

are they both called gnome panel? the one with "applications" and the one that has "show desktop" and the windows.

---

### Post by VMC on 2008-06-28
> **Phyrax said:**
> it's not the top panel it's the one at the bottom, so it seems to restart if i do that, but the other panel (the bottom one) is still there.

i also tried to end the process, but that didn't work.

are they both called gnome panel? the one with "applications" and the one that has "show desktop" and the windows.

Have you tried to click on the bottom panel and click on "New Panel"?

---

### Post by Phyrax on 2008-06-29
> **VMC said:**
> Have you tried to click on the bottom panel and click on "New Panel"?

no the panel is gone .....

---

### Post by Tomatz on 2008-06-29
The graphic i suspect is caused by awn not being run with a composting manager such as compiz.

Either enable/install compiz or use cairo dock which can be found in synaptic ;)

---

### Post by Phyrax on 2008-06-29
but i have compiz..

that's the thing that makes me have the workspaces cube right?

---

### Post by Tomatz on 2008-06-29
> **Phyrax said:**
> but i have compiz..

that's the thing that makes me have the workspaces cube right?

Yup :confused:


Can you post a screenshot of this graphic. Just press **<print screen>**.

---

### Post by Phyrax on 2008-06-29
[[IMG]http://img70.imageshack.us/img70/6488/screenshotgq0.th.png[/IMG]](http://img70.imageshack.us/my.php?image=screenshotgq0.png)

just under the first panel there. it's actually under the first panel too, it's like 2 panel length.

---

### Post by Tomatz on 2008-06-29
> **Phyrax said:**
> [[IMG]http://img70.imageshack.us/img70/6488/screenshotgq0.th.png[/IMG]](http://img70.imageshack.us/my.php?image=screenshotgq0.png)

just under the first panel there. it's actually under the first panel too, it's like 2 panel length.

Is awn running while this screenshot was taken?

---

### Post by Phyrax on 2008-06-29
yeah it was.

---

### Post by Tomatz on 2008-06-29
> **Phyrax said:**
> yeah it was.

Uninstall awn and install cairo-dock i think the problem is due to some weird bug in awn ;)

You can copy and paste the following into a terminal to do this:

```
sudo apt-get remove avant-window-navigator && sudo apt-get install cairo-dock cairo-dock-plug-ins
```

Then go to ***System, Preferences, Sessions*** and add the command **cairo-dock** to make cairo dock autostart.

Reboot ;)

---

