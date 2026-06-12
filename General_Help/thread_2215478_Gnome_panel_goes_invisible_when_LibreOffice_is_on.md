---
title: "Gnome panel goes invisible when LibreOffice is on"
date: 2014-04-06
forum: General Help
---

### Post by Peter_Brandon on 2014-04-06
I recently upgraded to 13.10 saucy.  Have been using it for a couple weeks and in the last couple days have had to use LibreOffice.  When LibreOffice is on, but not previously, gnome-panel and Docky become invisible.  I can still see tooltips and click on now-invisible icons (at random because I can't see them).  sudo killall gnome-panel doesn't fix this.  The panel and Docky aren't invisible the moment I turn on LibreOffice, but when I open, say, a new dialog box, they disappear.  They can also reappear periodically.  And, my mouse clicks don't seem to function properly in all cases even on visible window elements when the panel is gone.  Video freezes episodically with audio still going--problem disappears when I shift to another desktop and back.

Anyone have ideas about possible workarounds?

---

### Post by silex89 on 2014-04-06
Hi there!

This happens whenever you open LibreOffice? Do you see any flickering before the items dissapear?. Have you tried running LO in an unmaximized window to see if there's any other weird behaviour?.

I used to have this problem on my former laptop with Raring-dated packages, and moving around the LO window would restore the desktop to it's regular appearance.

---

### Post by Peter_Brandon on 2014-04-07
Hi silex89:  I never run LO in maximized windows.  I haven't seen a flicker either.  One moment the panels are there, the next they're gone.  Also, things begin to stop responding to mouse clicks, e.g. dialog box buttons.  The panels occasionally come back and click-ability sometimes returns, but then both go away again.  I can use the hide button on my lower panel to make it reappear again, but it generally disappears promptly as well.

I've tried the LO ppa for the current LO sequence, so 4.1.5--hoping that maybe the LO people have fixed this.  Get the same problem.

---

### Post by silex89 on 2014-04-11
Strange....Are you using gnome panel with Compiz effects enabled? What happens if you switch to the Metacity WM in the Classic Session with no effects?

Are you using proprietary driver for your graphic card?

---

### Post by Peter_Brandon on 2014-04-19
Hi silex89:  Thanks again for your replies!  I'm using gnome-panel in a classic gnome session with no effects (that's what it says).  Compiz is installed, but ps aux doesn't show it running.  Metacity is running.  On the other hand, from the behavior of my Docky app, it looks like compositing is on.  Not quite sure how to turn that off, if it would make a difference.

---

### Post by Peter_Brandon on 2014-04-20
I did a clean install of 14.04.  The problem seems to be gone.

Thanks!

---

### Post by mörgæs on 2014-04-20
Good, please mark the thread 'solved'.

---

