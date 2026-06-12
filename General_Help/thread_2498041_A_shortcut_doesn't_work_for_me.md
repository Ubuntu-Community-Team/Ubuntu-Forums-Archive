---
title: "A shortcut doesn't work for me"
date: 2024-05-27
forum: General Help
---

### Post by whk102 on 2024-05-27
I have tried to create a shortcut icon for an application without having superuser privileges, I have created a .desktop file in ./local/share/applications but it does not appear in the list of Ubuntu applications when I press the applications icon in the dock.

```

me@pc:~/.local/share/applications$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 24.04 LTS
Release:    24.04
Codename:    noble

me@pc:~/.local/share/applications$ cat foo.desktop 
[Desktop Entry]
Name=Kung Fury: Street Rage - Ultimate Edition
Comment=Play this game on Steam
Exec=flatpak run com.valvesoftware.Steam steam://rungameid/373180
Icon=org.gnome.SystemMonitor
Terminal=false
Type=Application
Categories=Game;

me@pc:~/.local/share/applications$ stat foo.desktop 
  Fichero: foo.desktop
  Tamaño: 600           Bloques: 8          Bloque E/S: 4096   fichero regular
Device: 252,1    Inode: 76584046    Links: 1
Acceso: (0644/-rw-r--r--)  Uid: ( 1000/ me)   Gid: ( 1000/ me)
Acceso: 2024-05-27 16:39:38.082282964 -0400
Modificación: 2024-05-27 16:39:26.640366376 -0400
      Cambio: 2024-05-27 16:39:32.908320680 -0400
    Creación: 2024-05-27 16:39:26.640366376 -0400

me@pc:~/.local/share/applications$ update-desktop-database
me@pc:~/.local/share/applications$ reboot

```

After creating the test file I restarted the computer but it still does not appear in the list of applications.

What did I do wrong?

---

### Post by vanadium on 2024-05-30
For a .desktop launcher to appear in the user menu, the "Exec=" field must point to a valid executable, and there must be "Name=" and "Type=Application" lines. I cannot see anything that could be wrong in your .desktop file and where you placed it. 

In principle, the icon should appear within seconds after installing or updating the .desktop file. To make sure, try logging out then back in.

- Does the command "which flatpak" indeed yield the path to the flatpak executable?

- Check whether the command after "Exec=" runs correctly if you copy it from the file, then run it in the terminal.

- Although I don't think that can be the issue, temporarily change the name from "Kung Fury: Street Rage - Ultimate Edition" to "Kun Fury", i.e., removing the colon and the dash. Or try placing the name between quotes.

---

### Post by whk102 on 2024-06-04
I solve problem adding the execute permission to desktop file: chmod +x file.desktop

---

### Post by vanadium on 2024-06-06
That should not be necessary. Perhaps this is after you logged out then back in.

---

### Post by ActionParsnip on 2024-06-06
Yeah was going to suggest executable-ness

---

