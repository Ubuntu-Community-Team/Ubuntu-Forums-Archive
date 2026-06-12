---
title: "Moving icons from desktop"
date: 2020-06-01
forum: General Help
---

### Post by wmrp on 2020-06-01
Just getting started with Ubuntu (20.04)
I am trying to move the Trash and <user> icon from the desktop to the taskbar. Any suggestions as to how to do that? Thanks!

---

### Post by Dennis N on 2020-06-01
Turn off trash icon and personal icon using Tweaks > Extensions > Desktop Icons (config button) > Icon(s) on/off
Is 'Task bar' you refer to the 'Dash to Panel' extension? If so, I've not used that extension, but check it's configuration options.
If you want trash icon on top panel, that is supposed to be possible with another extension 'Trash' by bertoldia. Install it and see how it works.

---

### Post by wmrp on 2020-06-02
Would that be Gnome Tweaks (under Ubuntu Software)? By "task bar" I meant the "Dock". Is that what you call "top panel"?

---

### Post by deadflowr on 2020-06-02
The dock is the app listing panel on the left.
You cannot put files or folder there, it's for applications only.
You can however enable trash on it.
Unfortunately the dock settings are rather paltry on Ubuntu,
but the underlyng ability to do so is available.

You can use either dconf-editor (needs to be installed.)
This is a graphical program.
To enable trash in dconf-editor you need to click on org, then on gnome, then on shell, then on extensions, then on dash-to-dock, then finally scroll all the way down to show-trash and toggle the button to on.

Or run
```
gsettings set org.gnome.shell.extensions.dash-to-dock show-trash true
```
this will place a trash folder in the dock.


Of course if you're actually meaning dock as in the top panel, then that's something different.

---

### Post by Dennis N on 2020-06-02
If you want Trash Icon on the Dock, you can also do this from the Dash-to-Dock configuration settings in **Tweaks > Extensions > Dash to Dock > Config (Icon) > Launchers (Tab) > Show Trash Can (checkbox)**. You must have Dash to Dock extension installed and active.

---

