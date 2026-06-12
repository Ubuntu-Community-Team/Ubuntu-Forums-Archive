---
title: "Taskbar blocks windows since it's on the bottom"
date: 2018-09-28
forum: General Help
---

### Post by dexterlab977 on 2018-09-28
I have moved my taskbar to the bottom cause I got used to it as the default for Xubuntu is on top. Now the panel/taskbar would get in the way of the windows when I maximize the windows. I can minimize and resize it manually so it won't stand in the way of the taskbar, but it's annoying AF to do so manually. So what's the fix?


[IMG]http://i64.tinypic.com/iy1mz5.png[/IMG]

---

### Post by ajgreeny on 2018-09-29
If you want the panel hidden by a maximised window, that is not the normal way that the xfce4-panel (or any other of the DE panels) works; for that you need to go to full-screen.

If I misunderstood what you want tell us more.

---

### Post by The Cog on 2018-09-29
The problem I see is that the bottom of the window is at the bottom of the screen, not resting on the top of the panel (I can see the right-hand scrollbar arrow behind the panel). That does not happen on my xubuntu - on mine, the bottom of the window touches the top of the panel. Maybe it's a problem with a particular theme. Here I am using Clearlooks-Phenix theme in Appearnce, and Wallis style in Window Manager. How about you?

---

### Post by Holger_Gehrke on 2018-09-29
There's one option in the panel settings you might want to check. In the German translation of XFCE it's called "Keinen Platz an den Rändern reservieren" ("Don't reserve space at the edges"). If this is set, I get the behaviour your screenshot is showing. By default this is not set, but you might have set it while trying to get the panel to move. The attached screenshot shows the panel settings with that option highlighted.

Holger

---

### Post by dexterlab977 on 2018-09-29
That fixed it, must have messed something up at the beginning

---

