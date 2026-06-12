---
title: "Problem: Exit tsclient fullscreen mode in fluxbox"
date: 2008-04-21
forum: General Help
---

### Post by leeyee on 2008-04-21
Hi guys,

I've just managed to connect remote winXP with tsclient in fluxbox, but problem comes out that i cannot exit fullscreen mode back to FLUXBOX except disconnect RDP. I've googled a lot, Ctrl+Alt+Enter didn't work here, it just flashed, nothing happened then. And i also checked up "Enable Window Manager Key Binding" & "Attach to Console" options in tsclient->performance tab.

I was wondering it might be shortcut problem in fluxbox, so I checked .fluxbox/keys, it gives
```
OnDesktop Mouse1 :HideMenus
OnDesktop Mouse2 :WorkspaceMenu
OnDesktop Mouse3 :RootMenu
OnDesktop Mouse4 :NextWorkspace
OnDesktop Mouse5 :PrevWorkspace

Mod1 Tab :NextWindow
Mod1 Shift Tab :PrevWindow
Mod1 F1 :Workspace 1
Mod1 F2 :Workspace 2
Mod1 F3 :Workspace 3
Mod1 F4 :Workspace 4
Mod1 F5 :Workspace 5
Mod1 F6 :Workspace 6
Mod1 F7 :Workspace 7
Mod1 F8 :Workspace 8
Mod1 F9 :Workspace 9
Mod1 F10 :Workspace 10
Mod1 F11 :Workspace 11
Mod1 F12 :Workspace 12

```

Anybody knows how to figure this out? Thank you!

---

### Post by ryanhaigh on 2008-04-21
From the manpage for rdesktop (thats the program that is used by tsclient to connect to windows remote desktop protocol servers)

> Fullscreen mode can be toggled at any time using Ctrl-Alt-Enter.

---

### Post by leeyee on 2008-04-22
Ctrl+Alt+Enter didn't work here, it just flashed, nothing happened then.

---

### Post by ryanhaigh on 2008-04-22
The only thing I can suggest is to look through the documentation for rdesktop, go to system>help and support and search for man rdesktop to bring up the manual page. Using rdesktop directly rather than through tsclient isn't particularly difficult. Sorry I can't be of more assistance as I don't have a windows machine anymore to connect to so as to test anything.

---

### Post by leeyee on 2008-04-23
Hey, thanks for your reply.
Now I am sure the problem comes from fluxbox. I just quit X, re-enter into Gnome and "Ctrl+Alt+Enter" worked in Gnome. But in fluxbox, it just flashed~

I also tried manually connect use rdesktop like this:
```
rdesktop -f -u xxxx -p xxxx 172.xxx.xxx.xxx
```
but still cannot exit fullscreen in it. Any idea?

Thank you!

---

### Post by ryanhaigh on 2008-04-23
Perhaps fluxbox binds that key combination to another command specific to the window manager, I don't know how you could check for this though. Perhaps you could use something like wmctrl to resize the window? Is there a way to bring up a rdesktop menu like F8 does in vnc?

---

### Post by leeyee on 2008-04-28
After upgraded to 8.04, it suprised me that i can now get back to fluxbox use Alt+F1, which means switch to workspace 1 as defined in ~/.fluxbox/keys.(I normally connect remote computer in workspace2)

---

### Post by ryanhaigh on 2008-04-28
I just read in another thread that starting rdesktop with a set geometry and then using ctrl+alt+enter to get to fullscreen allows you to change back as well.

---

