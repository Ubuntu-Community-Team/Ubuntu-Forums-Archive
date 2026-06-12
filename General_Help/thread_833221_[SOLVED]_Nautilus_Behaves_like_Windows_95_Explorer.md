---
title: "[SOLVED] Nautilus Behaves like Windows 95 Explorer"
date: 2008-06-18
forum: General Help
---

### Post by jpietari on 2008-06-18
My Nautilus behaves really weirdly in Ubuntu 8.04.  I think it is a configuration thing, but I can't seem to find it.  Here is what is happening:

1. I do not have the toolbar that is on the left-hand side
2. When I double-click a folder, a new Nautilus window is opened
3. The location bar is in minimal state at the bottom of the screen

This happens when I log in NOT as an admin user (i.e. cannot update packages).  Configuration options on my Nautilus menu bar seem to be missing too.

See the attached screen shot to see what I'm getting

---

### Post by kerry_s on 2008-06-18
try clicking view> ...

---

### Post by jpietari on 2008-06-18
I'm unable to see all the options under the "View" menu.  If I could enable all the options under the "F9" shortcut, this would fix my problem.  

Please see my attached screen shots.

Maybe its a security thing that I can configure under "Authorizations" (PolicyKit)?!?!?

---

### Post by NilsE on 2008-06-18
Go into the configuration editor and under 

apps > nautilus > preferences 

and see if any of those help you turn on the 4 options that should be in the view menu.

It may help to run gconf-editor with gksudo in a terminal.

gksudo gconf-editor

---

### Post by mannheim on 2008-06-18
In Nautilus, go to "Edit-->Preferences" and select the "Behavior" tab. Then check the box for "Always open in browser windows".

---

### Post by jpietari on 2008-06-18
Thanks NilsE & mannheim.  

Enabling the "Always open in browser windows" fixed the problem.  I tell ya, I learned a lot more about Ubuntu on this one.  I was digging in the registry and looking at hidden files in my home directory.

Thanks again...:)

---

