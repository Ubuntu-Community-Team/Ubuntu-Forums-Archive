---
title: "Can't costumize gnome panel"
date: 2008-05-21
forum: General Help
---

### Post by mkljun on 2008-05-21
Hi.

Since I upgraded to 8.04 I can't do anything on the Gnome panel. The only two options I get when I right click on any panel are About and Help. 

No Properties, no Add, no Remove, ...

Any suggestion what might resolve the problem?

On the Launchpad I found a similar case but the guy wanted to remove the panel but had the same problem as me:
[https://answers.launchpad.net/ubuntu/+source/gnome-panel/+question/26740](https://answers.launchpad.net/ubuntu/+source/gnome-panel/+question/26740)
But I don't want to remove the panel. I just want my properties back :).

lp mk

---

### Post by Forlong on 2008-05-21
Are you able to drag and drop icons from the menu to the panel?

---

### Post by N.N. on 2008-05-21
It sounds like your gnome-panel is locked down. You can remedy this from gconf-editor. Start it from the quick launch dialogue (ALT+F2) or from the terminal: ```
gconf-editor
``` Once the editor has opened, navigate to "apps" > "panel" > "global", and uncheck the key called "locked_down".

Alternately, issue the following command in a terminal. (It does the same thing): ```
gconftool -t bool -s /apps/panel/global/locked_down false
```

---

### Post by mkljun on 2008-05-21
Forlong: nope .. I couldn't do anything with the menu.

N.N.: Thank you so much :)! That solved the problem. I was searching through keys in gconf-editor but I didn't find a solution.

After changing the key, the panel must be restarted, which can be done with the following command:

```
killall gnome-panel
```

lp mk

---

### Post by N.N. on 2008-05-21
You're welcome. :)

---

