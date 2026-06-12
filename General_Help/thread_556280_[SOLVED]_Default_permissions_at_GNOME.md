---
title: "[SOLVED] Default permissions at GNOME"
date: 2007-09-21
forum: General Help
---

### Post by nvteighen on 2007-09-21
I've noticed that GNOME doesn't respect my default umask 077 set at ~/.bashrc (and terminal does), so if I create a file with Open Office or a folder with Nautilus or whatever other GUI app, it behaves as it had umask 022. But, if I use nano, vi or whatever other CLI app, I have the permissions I want.

Does anyone know how to do this **user-wide** (not system-wide)? I've searched at my home folder, at gconf-editor and Nautilus preferences and haven't seen any file or entry that sets a "umask" at GNOME the way bash does.

---

### Post by nvteighen on 2007-09-22
I've solved it! I put it here so anyone can see it.

The idea is this: a umask at the .bashrc file manages permissions for terminal and console; .profile manages it for GNOME.

So, if you want a default umask 022 for GNOME, open ~/.profile with your favorite text editor, add "umask 022" (without quotes) at the end, save and restart X (Ctrl+Alt+Backspace).

---

