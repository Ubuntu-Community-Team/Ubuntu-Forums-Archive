---
title: "All windows disappear (but are still running) and screen wallpaper resets"
date: 2014-01-23
forum: General Help
---

### Post by scottbomb on 2014-01-23
Twice in the past few days, I have run into a most odd situation. I work with 2 monitors and multiple windows open. All of a sudden, all of my windows disappear and the wallpapers revert to the default purple Kubuntu wallpaper. The buttons on the taskbar for each open program are gone, as if I had closed all of the windows. However, the programs are indeed still running. I can tell because I can still hear the audio from a video I am streaming. Alt-tab doesn't show any of them. It's as if the running programs are invisible to the GUI. I do not use multiple desktops, however the behavior is similar to what happens when you do switch desktops. The only way to recover is to reboot. When I do reboot, I have to go in and change my wallpaper back to what I normally use (custom images) as Kubuntu seems to have forgotten my wallpaper settings.

Any ideas on what's causing this or what I should file a bug against? Is there a way to recover without rebooting? Unfortunately, I haven't been able to reproduce the problem on demand. I thought there may be a key combination that I had inadvertantly depressed but again, I cannot seem to reproduce this condition when I try random key combinations.

---

### Post by scottbomb on 2014-01-31
Well it happened again today, even after a fresh re-install last night (different reason). I think it has something to do with a key combination on the lower-left side of the keyboard but I can't seem to reproduce it on purpose.

---

### Post by scottbomb on 2014-02-03
This is NUTS. It happened again today. I cannot work like this. Going back to Xubuntu. I LOVE how KDE looks but I need stability.

---

### Post by scottbomb on 2014-05-27
OK, finally found the source of the problem. It's a KDE/Kubuntu feature! I was accidentally hitting the "super" aka "meta" (Windows) key while hitting tab. Apparently that causes the machine to shift workspaces. I don't use multiple workspaces. Was able to disable this by going into the Global Keyboard Shortcut settings and changing the hotkey to "none" for Activities, Next Activity, and Previous Activity under KDE Component Plasma Desktop Shell.

---

