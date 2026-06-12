---
title: "mythtv fullscreen problem"
date: 2006-11-09
forum: General Help
---

### Post by Naegling23 on 2006-11-09
Im having a problem with mythtv.  Im running kde and beryl on aiglx.  Mythtv goes fullscreen, but behind my panels.  How can I convince it to run over top of them.  My other programs, games, tvtime work fine in fullscreen mode.

---

### Post by xinix on 2006-11-09
One way would be to allow apps to be on top of panels. Another option would be to auto hide you panels.  To set this, right click on the panel> unlock panel if needed> Configure Panel> Hiding.

There may be a better way to do this but I never figured it out.  Didn't try much either.  I like hiding my panel.

---

### Post by superm1 on 2006-11-09
Tweaking the settings about running the frontend in a window, should change this behavior to my knowledge.  I had something similar happen in gnome, but I have to double check the solution.

---

### Post by Naegling23 on 2006-11-11
Well, I can hide my panels, but then I have that annoying little square on the side of the screen, plus I have to manually hide the panels whenever I start the program.  Having all programs cover them doesnt work, because then they get covered up by other programs.  Im aware of the workarounds, but im really looking to "fix" the problem.  Thanks for the reply though.

Hmm, Ive been playing around with running it in a window, and the other frontend settings, so far, no luck, although there may be one that I'm missing.  Currently, if I set it to run in a window, it runs fullscreen, minus the space taken up by my panels.  If I set it not to run in a window, it runs behind my two panels, and I have to hide them to see the full screen.

hmmm, Ill keep plugging away, something tells me I'm not the only person with this problem

---

### Post by RiCkY82 on 2006-11-20
Hi,

I got the same "problem". This is what I did to fix it.

Run mythfrontend

Then go to Utilities/Setup - Setup - Appearance - Screen Settings window. There you've got an option "Run the frontend in a window". Uncheck this and restart mythfrontend. Now it should run in Full Screen :)

Good luck,

Rick

---

### Post by hotani on 2006-11-20
Mine is the same way - I'll try playing around with the window settings when I get home tonight and see if that works.

This is only when running mythfrontend on mine - when watching a video it does go full screen with no panels.

---

### Post by RiCkY82 on 2006-11-20
I've just compiled the newest MythTV. Here the option i described aboved is unchecked by default. Too bad Ubuntu doesn't got this in apt...

---

### Post by superm1 on 2006-11-21
If you unchecked the option on the repository version, and then compiled your own version, did you share the same settings table?  The option would have remained.  I don't believe any particular settings like that are "ubuntu" specifically enabled or disabled at this point.

---

