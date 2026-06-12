---
title: "emacs causes gnome to hang"
date: 2006-12-29
forum: General Help
---

### Post by asubedi on 2006-12-29
My desktop completely freezes for few seconds when I click anywhere on the gnome panel while I am using emacs-snapshot. Does anyone experiences this?

---

### Post by cayhorstmann on 2007-10-29
Yes, I get that too, both with the emacs snapshot and with Emacs 23. It is very irritating. It is more than a few seconds for me, and I end up doing Ctrl+Alt+F1 followed by Ctrl+Alt+F7 to break out of it.

---

### Post by legrandyon on 2007-10-31
Hi,
I have similar problems. My favorite text editor is emacs and I have the version 22 running under 7.10 but since I installed it it causes my PC to freeze. No keyboard shortcut can allow me to get back a little bit of control on the PC and I have to turn it off !!
Does anybody know the reason(s) ? Is it due to the new version of Ubuntu or of emacs ? I never had this problem on my laptop running under 7.04 (I don't know what version of emacs was installed).
LGY

---

### Post by cayhorstmann on 2008-01-06
Specifically, the "Window Selector" and "Force Quit" panel items are problematic. Click on the Emacs window, then on either one--instant hang. Remedy: Ctrl+Alt+F1 and pkill gnome-panel.

---

### Post by nwillis on 2008-01-15
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/emacs22/+bug/183245](https://bugs.launchpad.net/ubuntu/+source/emacs22/+bug/183245) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I get this too, and I've opened a Launchpad bug on it to shed some light: [https://bugs.launchpad.net/ubuntu/+source/emacs22/+bug/183245](https://bugs.launchpad.net/ubuntu/+source/emacs22/+bug/183245)

N

---

