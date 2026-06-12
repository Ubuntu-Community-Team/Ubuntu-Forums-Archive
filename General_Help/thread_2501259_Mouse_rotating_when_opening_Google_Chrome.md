---
title: "Mouse rotating when opening Google Chrome"
date: 2024-09-29
forum: General Help
---

### Post by ciko1 on 2024-09-29
Hi

When i open google Chrome, my mouse keeps rotating like 20+ seconds: after rotating stops i can click on google chrome again. 
i disabled accelration, it did not help


this part helped:
i created a shortcut:
i configured a shortcut on the destkop: followed instruction from this site: [https://linuxconfig.org/how-to-create-desktop-shortcut-launcher-on-ubuntu-22-04-jammy-jellyfish-linux](https://linuxconfig.org/how-to-create-desktop-shortcut-launcher-on-ubuntu-22-04-jammy-jellyfish-linux)
and set [COLOR=var(--black-600)][FONT=var(--ff-mono)]StartupNotify=**true** to [/FONT][/COLOR][COLOR=var(--black-600)][FONT=var(--ff-mono)]StartupNotify=**false** 

the shortcut on the destkop worrks great and i have no rotation problems any more.


when i open the shortcut it apperas on the taskbar: i can pin it to the dash: after this the problem occurs again. 

so when i open google crhome from dash/taskbar i get the rotation problem, with the created shortcut on the destkop the problem dissapears.

is there any solution i can configue, so i can start the google grome from dash/taskbar?[/FONT][/COLOR]

---

### Post by adhesivereading on 2024-09-30
You can create or modify the `.desktop` file for Google Chrome to include the `StartupNotify=false` option, similar to what you did with the desktop shortcut:
- Locate the file: `.desktop` files for applications are usually located in `/usr/share/applications/` or `~/.local/share/applications/`. Look for the file named `google-chrome.desktop`.
- Edit the .desktop file: Open the file in a text editor with root or user privileges: sudo nano /usr/share/applications/google-chrome.desktop or nano ~/.local/share/applications/google-chrome.desktop
- Find the line that says `StartupNotify=true` and change it to `StartupNotify=false`. If that line doesn't exist, you can add it to the `[Desktop Entry]` section: StartupNotify=false
- Save and exit: If using `nano`, save the changes with `CTRL + O`, then exit with `CTRL + X`
You may need to log out or reboot for the changes to take effect

[RIGHT][SIZE=1][[COLOR=#ecebe4]boxing random[/COLOR]]("https://boxingrandom.com")[/SIZE][/RIGHT]

---

