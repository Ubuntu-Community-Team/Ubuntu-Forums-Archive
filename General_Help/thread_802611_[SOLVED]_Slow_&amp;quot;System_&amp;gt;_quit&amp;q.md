---
title: "[SOLVED] Slow &amp;quot;System &amp;gt; quit&amp;quot; dialog"
date: 2008-05-21
forum: General Help
---

### Post by Centx on 2008-05-21
Title says it all. When i choose system > quit in the menus, the comp will freeze for roughly 30 seconds, and the dialog pops up. It only happens once, and all subsequent quit-dialogs pops up immediately. 

This is obviously quite irritating, and if anyone else have had the problem, please post so here, even if you don't have a solution.

tl;dr: quit dialog makes the comp freeze, solution appreciated.

Fairly hi-spec computer too, so it isn't because of the lack of resources.

---

### Post by chrisccoulson on 2008-05-21
Have you made any customizations to your GNOME session that involve things like removing certain services or startup programs?

---

### Post by ferchon03 on 2008-05-21
Enable POWER MANAGER under System->Preferences->Sessions. Then restart.

---

### Post by chrisccoulson on 2008-05-22
That's what I was thinking

---

### Post by anaconda on 2008-05-22
I have the same problem, but it takes about a minute before anything happens..
And that is why I prefer "sudo halt -h" for shutting down the computer, or Ctrl-Alt-Backspace, and "Shut Down" from there. 

Thanks for the suggestion. I will try to enable the power manager, Which I think I have disabled.

---

### Post by chrisccoulson on 2008-05-22
I'm pretty sure disabling gnome-power-manager will have quite a noticeable effect. AFAIK, gnome-power-manager is a core component on your desktop, so you should leave it running anyway. When you click the log-out button, it tries to talk to g-p-m over DBUS to check power options so it knows what buttons to put in the dialog (suspend / hibernate etc). If it isn't running, it will take a long time

---

### Post by anaconda on 2008-05-22
THANK YOU ALL!!

I thought that this problem was related to my USB-TV-card, which has caused all the previous versions of ubuntu to not be able to shutdown AT ALL if the TV-card was connected,
So I didn't even try to seach solutions for shutdown problems anymore..

Wow.  now it works, AND Hardy even shuts down with my TV-card connected!!! Unbeliavable!!

THANKS  ;D

---

### Post by Centx on 2008-05-22
Was the gnome-power-manager for me too. And here I thought I made my system more responsive by disabling session-startups :lolflag:

---

