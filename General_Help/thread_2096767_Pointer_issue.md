---
title: "Pointer issue"
date: 2012-12-20
forum: General Help
---

### Post by m3t4lm4n222 on 2012-12-20
Hi. WHen I move my mouse pointer all the way to the right of the screen it instantly jumps back to the left side of the screen. How the hell do I fix this??

---

### Post by cwsnyder on 2012-12-21
If you check your workspaces, you probably moved to the workspace to the right of your working workspace. If you move to the left, you will change workspaces back to the original workspace and enter from the right.

If you want to 'fix' this, simply remove the extra virtual workspaces from your desktop.

'This isn't a bug, it's a feature.'

---

### Post by slickymaster on 2012-12-21
It is probably intended behaviour. Check that you have this setup:
[LIST=1]
[*]In System Settings, Monitor tab, have a launcher placed on every screen
[*]In same dialog, have monitor sticky edges disabled
[*]Launcher is in autohide mode
[/LIST]

In this case, in order to reveal the launcher on the right monitor, there is a "mouse barrier" which if you push against it with a certain pressure will cause the launcher on the right monitor to appear. You can play with this pressure in the System Settings->Appearance->Behaviour tab, by moving the "Reveal Sensitivity" slider.

Note that moving the mouse from the left monitor to the right will experience no barrier - i.e. it will smoothly move.

Maybe this helps clarify the behaviour.

---

