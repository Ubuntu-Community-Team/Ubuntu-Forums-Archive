---
title: "Could not add application to the application database"
date: 2005-10-20
forum: General Help
---

### Post by temcat on 2005-10-20
I wanted to choose VLC for opening mp3 files (I have the old 0.8.2 version), but for some reason, when I choose Properties in Nautilus right-click menu and try to add VLC for GTK+, I get an error: "Could not add application to the application database". Why is that? Can it be because I don't have alsa or esd plugin for vlc installed?

---

### Post by Kyral on 2005-10-20
It might be because "VLC for GTK+" isn't really a program. Its more like a frontend to "VLC Media Player". Try selecting that instead

---

### Post by temcat on 2005-10-20
[QUOTE=Kyral]It might be because "VLC for GTK+" isn't really a program. Its more like a frontend to "VLC Media Player". Try selecting that instead[/QUOTE]

No, that's not the case here. What I get is totally weird. "VLC for GTK+" is actually wxvlc. When I choose "Set custom command" and enter wxvlc there, it works...

---

### Post by Kyral on 2005-10-20
Wierd....May want to file a bug report on that

Anyway if your way works go for it ;P

I know thats not much help but...

---

### Post by temcat on 2005-10-20
[QUOTE=Kyral]Wierd....May want to file a bug report on that

Anyway if your way works go for it ;P

I know thats not much help but...[/QUOTE]

I found out what's wrong. This is a VLC bug: it leaves a malformed mime association file in ~/.local/share/applications named "gvlc-usercustom-<number>.desktop" which has the following contents:

[Desktop Entry]
Name=VLC for Gtk+
Name[fr]=VLC pour Gtk+
Comment=Gtk+ multimedia player
Comment[fr]=Lecteur multim

And that's all. As for filing a bug, I can't - as I said, this is an old update-locked version of VLC (0.8.2).

---

