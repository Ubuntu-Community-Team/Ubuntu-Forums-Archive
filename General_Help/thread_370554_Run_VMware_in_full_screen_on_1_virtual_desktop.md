---
title: "Run VMware in full screen on 1 virtual desktop"
date: 2007-02-25
forum: General Help
---

### Post by srunni on 2007-02-25
Hi,

I use Windows in VMware quite a bit, and I was wondering if there's any way to run it in fullscreen mode on one of Ubuntu's virtual desktops, and switch between desktops (and thus between Windows and Ubuntu) without exiting fullscreen mode in VMware? This would be very helpful, if possible.

Thanks in advance for the help!!

---

### Post by n8bounds on 2007-02-25
Once you are in vmware's full screen, the only way to get out is to ALT + CNTRL, right?  Then you can't perform any keyboard shortcut to switch viewports/workspaces in gnome until you leave the virtual console.  I think what you want to do cant be done directly with one keystroke.

---

### Post by JohnPhys on 2007-02-26
I'm not certain on this, but if you have the vmware tools installed, it lets your mouse move out of the virtual machine without the ctrl+alt.  You might be able to set it so that moving the mouse off of the screen changes the workplace.

---

### Post by tagra123 on 2007-02-26
In gnome, if you set the lower panel to auto hide.

If the desktop resolution is 1024 X 768   then you can set the windows resolution to 1006 X 652 and it will almost apper full screen allowing the panels to be displayed.  The easier way is to set auto resizing.

I used VM workstation option to allow the window to auto resize.  Here's how to do it manually.

Close running vmplayer

```

cp ~/.vmware/preferences ~/.vmware/preferences.bak.original
gedit ~/.vmware/preferences
```

add or edit the following three lines.

```

pref.autoFitGuestToWindow = "TRUE"
pref.autoFitFullScreen = "fitHostToGuest"
pref.autoFit = "TRUE"

```

Save and exit

Restart vmplayer.

---

### Post by srunni on 2007-02-26
> **tagra123 said:**
> In gnome, if you set the lower panel to auto hide.

If the desktop resolution is 1024 X 768   then you can set the windows resolution to 1006 X 652 and it will almost apper full screen allowing the panels to be displayed.  The easier way is to set auto resizing.

I used VM workstation option to allow the window to auto resize.  Here's how to do it manually.

Close running vmplayer

```

cp ~/.vmware/preferences ~/.vmware/preferences.bak.original
gedit ~/.vmware/preferences
```

add or edit the following three lines.

```

pref.autoFitGuestToWindow = "TRUE"
pref.autoFitFullScreen = "fitHostToGuest"
pref.autoFit = "TRUE"

```

Save and exit

Restart vmplayer.

Actually, I know about this auto-resizing feature in VMware and I have it enabled. Also, I'm using KDE (not that that really matters lol). I was just wondering if it'd be possible to make it look like "real" parallel virtualization, because that'd be pretty cool. My final goal is to be able to boot my physical Vista partition in VMware with a graphics driver for it so I have the full Aero interface, and be able to have it as one side of a Beryl cube. That would be amazing.

---

