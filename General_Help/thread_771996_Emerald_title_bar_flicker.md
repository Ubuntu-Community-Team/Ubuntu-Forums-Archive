---
title: "Emerald title bar flicker"
date: 2008-04-28
forum: General Help
---

### Post by Jonothewright on 2008-04-28
Hi all

I recently upgraded to Hardy. Everything has been great except for this one little thing in Emerald: whenever I hover the cursor over any of the buttons in the title bar of the window it flickers. Not life threatening or drastic just kinda annoying. Strangely it seems to happen only when I have Open Office Word open, yet affects every window on the screen. Has anyone else out there had something like this? Any ideas what may be wrong?

Cheers

---

### Post by mpospisil on 2008-04-28
I have this same exact problem.  It seems to be really bad with Open Office Word. It also happens with firefox sometimes. I'm using Emerald as my window manager. The minimize and close buttons flicker when I hover the mouse over them.  Does anyone know how to fix this?

---

### Post by Ebuntor on 2008-05-01
I have the same problem. Seems not only Emerald flickers also the AWN dock has the same problems. It seems that when you've clicked on a text field in Firefox or OpenOffice the blinking cursor in the text field causes the flickering in Emerald.

---

### Post by Gavin77 on 2008-05-01
> **Jonothewright said:**
> Hi all

I recently upgraded to Hardy. Everything has been great except for this one little thing in Emerald: whenever I hover the cursor over any of the buttons in the title bar of the window it flickers. Not life threatening or drastic just kinda annoying. Strangely it seems to happen only when I have Open Office Word open, yet affects every window on the screen. Has anyone else out there had something like this? Any ideas what may be wrong?

Cheers

Open up Emerald Theme Manager, click on the "Emerald Settings" tab and untick "use button fade pulse", that should do it for you.

---

### Post by sebf_ on 2009-03-08
Sorry to bring up an old thread, but I had a similar issue with flickering title bars on windows in Ubuntu 8.10 (Intrepid Ibex). Happened with an old laptop with an nVidia GeForce Go 6200 graphics chip and heres how I fixed it:

[LIST=1]
[*]Install CompizConfig (via System->Administration->Synaptic Package Manager) 
[*]Install Emerald Theme Manager
[*]In System->Preferences->CompizConfig set Window Decoration Command to: **emerald --replace**
[*]In System->Preferences->Emerald Theme Manager (under settings tab) disable **Use Button Fade Pulse** (optional, but helps)
[*]In Emerald Theme Manager import: [URL="http://www.gnome-look.org/content/show.php?action=content&content=63725"]Human Orange (bottom round corners)
  theme[/URL]
[*]Restart your computer
[/LIST]

I couldn't seem to find the original Ubuntu Human Emerald window theme?
Now all I need to figure out is how to set the Compiz and Emeral settings as default for all users.

---

