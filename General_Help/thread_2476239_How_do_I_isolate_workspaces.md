---
title: "How do I isolate workspaces?"
date: 2022-06-20
forum: General Help
---

### Post by harisahmad on 2022-06-20
I want to have completely isolated workspace meaning I do not want any application in another workspace to appear in my current workspace. For example, I have a Firefox window open in Workspace 1 and when I open Firefox in Workspace 2, I do not want the computer to redirect me to Workspace 1, it should open a new window. How can I achieve that?

I am currently running Ubuntu 22.04 and I had isolated workspace setup in Ubuntu 20.04 and it worked completely fine. If I remember correctly I was using Dash to Dock extension, I cannot find it anymore on 22.04, so instead I am using Plank dock. It has an option called 'Restrict to Workspace' but it only restricts applications that are not pinned to the dock.

I have tried using these commands to no avail, any help would be appreciated.
```
gsettings set org.gnome.shell.app-switcher current-workspace-only true
gsettings set org.gnome.shell.extensions.dash-to-dock isolate-workspaces true
```

---

### Post by vanadium on 2022-06-21
For me, the dash-to-dock setting effectively isolates workspaces: when switching workspaces, running applications dissappear, clicking one of the favorites opens a new window on the current workspace. Ubuntu Dock is based on Dash to Dock and uses the same dconf settings.

---

### Post by Dennis N on 2022-06-21
>  I have a Firefox window open in Workspace 1 and when I open Firefox in Workspace 2, I do not want the computer to redirect me to Workspace 1, it should open a new window. How can I achieve that?
Just hold down the Control Key while clicking on the icon in the dock. This forces a new application window in the current workspace. This works with Dash to Dock, Plank, and probably other launchers. 
OR
Right click the icon to get the context menu, and there should be an option to 'open a in new window' or 'new window'.
Added:
Just noticed that if you right-click on an icon in the Applications Menu, the application opens a new window if it's already running. No context menu. (An Applications Menu is not installed by default. They are gnome-shell extensions.)

---

### Post by harisahmad on 2022-06-21
I know about that but it is harder to keep track of windows when I have so many windows open

---

### Post by Dennis N on 2022-06-21
Ctrl+Tab will show all windows on all desktops for each application as you cycle through the applications. Or use tabs if the application supports them. Many do, like terminal, Firefox, text editor.

---

### Post by vanadium on 2022-06-21
Did you try with Ubuntu dock?

---

