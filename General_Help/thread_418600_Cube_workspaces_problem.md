---
title: "Cube workspaces problem"
date: 2007-04-22
forum: General Help
---

### Post by qkmbr22 on 2007-04-22
Hi. just installed 7.04 today, enabled desktop effects with the cube. Everything worked fine at first. then i disabled the effects for a while and now I cannot get the cube to work. When I enable the desktop effects, I only get one workspace and the cube doesn't work. When I add workspaces manually, the cube still doesn't work. Can someone please help me?

---

### Post by theriesproject on 2007-04-24
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/desktop-effects/+bug/102309](https://bugs.launchpad.net/ubuntu/+source/desktop-effects/+bug/102309) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/desktop-effects/+bug/102309](https://bugs.launchpad.net/ubuntu/+source/desktop-effects/+bug/102309) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Try this, it worked for me:

System -> Preferences -> Desktop Effects

Only uncheck "Workspaces on a cube", leave desktop effects on.

Right click the Workspace Switcher on the taskbar, choose Preferences.

Increase the number of Workspaces (not the number of rows) to 4 and Close

Go back to Desktop Effects and Enable workspaces on a cube and click close.

Cube should work now.

This is a known bug, opening Desktop Effects changes the number of workspaces to 1, no matter what you choose.

---

