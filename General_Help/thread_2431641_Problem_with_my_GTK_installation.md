---
title: "Problem with my GTK installation"
date: 2019-11-19
forum: General Help
---

### Post by goemonburo on 2019-11-19
So in trying to sleuth a problem someone posted to me that this wasn't a bug with their program but rather something wrong with GTK.  I don't know if that's true or not but perhaps someone out there will help me:

The issue has happened on several different programs (so it may indeed be a system related issue!).  I'm running vanilla Lubuntu 18.04LTS, nothing crazy.  Consistently, when the issue happens (and it happens every time on Bluefish and RedNotebook), the sidebar and header appear fine, but the main pane of the window is transparent:  its background, instead of being legible white and black, is like a screenshot of the window behind it when the app opened.  If I move the window that pane stays "frozen."  I can write in it, but the text quickly becomes illegible because nothing typed is ever reset to white...the cursor ghosts, the text remains ghosted if I delete or scroll...so essentially it's unusable.  

In Bluefish I fixed the problem by using their preferences to set the background default to white.  (Not sure what it was originally.)  Problem solved.

RedNotebook, however, doesn't have that option so I'm stuck unless someone knows what to change to make GTK (if it IS that) work correctly.

Thank you in advance.

---

### Post by goemonburo on 2019-11-21
I believe I have fixed the problem by installing a GTK3-compliant theme.  Apparently the default Lubuntu theme was not, and it caused issues.  I installed (first installing gnome-tweaks, then installing Arc theme via apt-get install, then applying Arc theme using Tweaks) the Arc theme.  I liked the default Lubuntu theme a little better but this works and now I do not have the problem described above anymore.  Hope this is useful for others out there.

---

