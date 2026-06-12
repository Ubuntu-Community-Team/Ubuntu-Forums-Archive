---
title: "Broken Workspace Switcher 8.04"
date: 2008-06-13
forum: General Help
---

### Post by kbow on 2008-06-13
I can't click on my workspaces to move to new workspaces. But I can move windows over there, at least it seems that I can because they disappear and I can see the icon moved over.

I used these instructions below when working with desktops



To have different wallpapers for each desktop, follow these steps:

I. Disable "show desktop" in Nautilus
1. ALT+F2
2. gconf-editor
3. Apps --> Nautilus --> Preferences
4. Untick "show desktop"

II. Install Compiz Fusion
1. In Terminal, input the following:
Code:

sudo aptitude install compizconfig-settings-manager

2. Exit Terminal

III. Select your desktop wallpaper
1. System --> Preferences --> Advanced Desktop Settings
2. Tick "Desktop Cube" and opt to disable desktop wall if prompted
3. Tick "Rotate Cube"
4. Select "Desktop Cube"
5. Click "Appearance" tab
6. Click "Add" under the "Background Images" field
7. Browse for your desired wallpaper(s), ordering them based on which face of the cube you want them to appear


After this did not work well, I then did 

sudo aptitude remove compizconfig-settings-manager


Now my workspace switcher is broken, as I used to be able to click on the workspace, or roll my scroll wheel forward to move over.

Can anyone help to get my Ubuntu back the way it was ?

---

### Post by sdennie on 2008-06-13
You should reinstall compizconfig-settings-manager and make sure that the Viewport Switcher plugin is enabled (it's near the cube options).

---

### Post by kbow on 2008-06-17
Plugin is enabled, still not able to do any switching.

---

### Post by Nameless Neko on 2008-06-26
> **kbow said:**
> Plugin is enabled, still not able to do any switching.Enable Desktop Wall and Viewpoint Switcher in that menu.  That enables the full functionality of the workspace switcher on the panel, and with the mouse wheel.

---

