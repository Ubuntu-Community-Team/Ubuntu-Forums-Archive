---
title: "[SOLVED] Gnome Keyboard properties preview"
date: 2008-06-28
forum: General Help
---

### Post by Elfy on 2008-06-28
Has anyone seen this on Hardy ?

When I try to change keyboard layout, the preview window doesn't show the new layout and shows the results from the drop down menus.

It isn't actually a problem as such as I was just looking for someone else, but if it is a bug it will need reporting I guess.

---

### Post by Elfy on 2008-07-23
bumpity bumpity bump

---

### Post by Elfy on 2008-08-08
bump

---

### Post by darylb on 2008-08-11
Yes I have seen this too. Along with the annoying "Error activating XKB configuration." It is mentioned in 
[this]("https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/221196") bug.

---

### Post by Elfy on 2008-08-11
Thanks - hadn't found that bug. Added on the end but it's low priority :)

---

### Post by darylb on 2008-08-11
You're using the gnome desktop right? So am I, but because I like K3B I also have some KDE libs installed. I was just hunting around my menu and found this under "Applications -> Other -> Keyboard Layout". It is a KDE program and the launcher translates to this command:
```
kcmshell keyboard_layout
```
When I played about in there I managed to get the layouts showing up again in the gnome-keyboard-properties app (not sure how exactly). I was also able to use the KDE tool to sucessfully change the layout whereas I only get the "Error activating XKB configuration." when using the gnome app. Maybe they conflict. I'd uninstall the KDE libs to see but then I'd loose K3B so I've just changed my layout with the KDE tool for now. It works so I'm happy :) Hope the same might work for you.

---

### Post by Elfy on 2008-08-11
Yes - in the same boat, so I had that kde as well - I don't actually need to change my keyboard at all - I didn't find the bug until I was helping someone else, as it is reported as a bug I've actually found out now the answer to my original query so I can mark it solved I think.

But thanks for your help - it was appreciated :)

---

