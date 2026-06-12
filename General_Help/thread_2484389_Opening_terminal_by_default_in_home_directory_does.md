---
title: "Opening terminal by default in home directory does not work"
date: 2023-02-24
forum: General Help
---

### Post by freddybz on 2023-02-24
[COLOR=#232629][FONT=-apple-system]I am using Ubuntu 22.04. The terminal that it opens from desktop context menu is the gnome-terminal. By default it opens it on the ~/Desktop directory. I want to modify the default directory **without** changing .bashrc. I've encountered a suggestion to add --working-directory=$HOME to the "Exec" entry of /usr/share/applications/org.gnome.Terminal.desktop. It does not work - the terminal still opens on "~/Desktop".[/FONT][/COLOR]
[COLOR=#232629][FONT=-apple-system]Any ideas?[/FONT][/COLOR]
[COLOR=#232629][FONT=-apple-system]Freddy[/FONT][/COLOR]

---

### Post by MAFoElffen on 2023-02-25
In my .desktop file for /usr/share/applications/org.gnome.Terminal.desktop
```

[Desktop Entry]
Name=Terminal
Comment=Use the command line
Keywords=shell;prompt;command;commandline;cmd;
TryExec=gnome-terminal
Exec=gnome-terminal
Icon=org.gnome.Terminal
Type=Application
Categories=GNOME;GTK;System;TerminalEmulator;
StartupNotify=true
StartupWMClass=Gnome-terminal
X-GNOME-SingleWindow=false
OnlyShowIn=GNOME;Unity;
Actions=new-window;preferences;
X-Ubuntu-Gettext-Domain=gnome-terminal

[Desktop Action new-window]
Name=New Window
Exec=gnome-terminal --window

[Desktop Action preferences]
Name=Preferences
Exec=gnome-terminal --preferences [COLOR=#ff0000]--working-directory=/home/mafoelffen/Scripts[/COLOR]

```

---

### Post by coffeecat on 2023-02-25
Also posted on AskUbuntu: [https://askubuntu.com/questions/1456579/opening-terminal-by-default-in-home-directory-does-not-work](https://askubuntu.com/questions/1456579/opening-terminal-by-default-in-home-directory-does-not-work)

---

### Post by mIk3_08 on 2023-02-25
> **freddybz said:**
> [COLOR=#232629][FONT=-apple-system]I am using Ubuntu 22.04. The terminal that it opens from desktop context menu is the gnome-terminal. By default it opens it on the ~/Desktop directory. I want to modify the default directory **without** changing .bashrc. I've encountered a suggestion to add --working-directory=$HOME to the "Exec" entry of /usr/share/applications/org.gnome.Terminal.desktop. It does not work - the terminal still opens on "~/Desktop".[/FONT][/COLOR]
[COLOR=#232629][FONT=-apple-system]Any ideas?[/FONT][/COLOR]
[COLOR=#232629][FONT=-apple-system]Freddy[/FONT][/COLOR]
In  my case, I usually use to open terminal via ctrl + alt + t in Desktop  environment and it will automatically opens to $HOME directory. But If I  right click in Desktop environment and then use the "Open in Terminal"  that will open from the Desktop Directory "~/Desktop". Regards and cheers

---

### Post by Impavidus on 2023-02-26
If you right-click in some directory, then ask to open a terminal there, it will give you a terminal with the present working directory set to that directory where you opend it. And the desktop is the ~/Desktop directory. It's a feature.

---

