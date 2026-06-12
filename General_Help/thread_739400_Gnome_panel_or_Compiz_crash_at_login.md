---
title: "Gnome panel or Compiz crash at login?"
date: 2008-03-29
forum: General Help
---

### Post by DarkOx on 2008-03-29
I recently switched from Kubuntu to Ubuntu (clean install, Gutsy). So far, Gnome's been great -- except for an issue I seem to be having 15-20% of the time when I log in. 
[LIST]
[*]The Gnome panel won't load -- it'll just be a solid beige bar with no menus or anything appearing on it. Clicking anywhere on it doesn't seem to do anything.
[*]My keyboard won't respond to any inputs. Ctrl+Alt+Backspace doesn't do anything, nor can I use Gnome-Do to bring up any programs.
[*]I have Desktop Effects enabled, and Compiz seems to be working fine (at least, I can use the middle mouse button to move the cube, since the keyboard won't let me switch desktops)
[*]Applications, should I click them from the AWN panel, don't appear. Since I can't load anything or input anything, I have to do a hard reboot and hope the issue doesn't happen again.
[/LIST]

I'm not entirely certain what's causing the problem. I would have figured this was a Compiz thing, but Compiz seems to be working fine. Maybe the panel is crashing? I haven't been able to find anything on Launchpad, Google or the forums that match my symptoms. Has anyone experienced something similar? Or does anyone know how I'd go about diagnosing exactly what the problem is?

---

### Post by CLomax on 2008-03-31
I had a similar problem, a crash would ensue every time I logged back in for some reason or another. I solved it by adding Compiz and Emerald to the startup programs list in System -> Preferences -> Sessions.

> Name: Compiz
Command: compiz --replace

> Name: Emerald
Command: emerald --replace

This prevents Compiz or Emerald from stopping the log in process. Give it a try.

---

