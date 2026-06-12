---
title: "No system startup sound heard"
date: 2021-05-31
forum: General Help
---

### Post by SciGuy1872 on 2021-05-31
Hi.  
> anthony@anthony-Latitude-E5420:~$ ls /usr/bin/canberra-gtk-play/usr/bin/canberra-gtk-play
> /usr/bin/canberra-gtk-play

> anthony@anthony-Latitude-E5420:~$ ls /usr/share/gnome/autostart
libcanberra-login-sound.desktop  Caja shows the name of the file at that path as "GNOME Login Sound"

Here's the contents of GNOME Login Sound--I made some changes.
> [Desktop Entry]
Type=Application
Name=GNOME Login Sound
Comment=Plays a sound whenever you log in
Exec=/usr/bin/canberra-gtk-play --id="desktop-login" --description="GNOME Login"
OnlyShowIn=GNOME;Unity;
AutostartCondition=GSettings org.gnome.desktop.sound event-sounds
X-GNOME-Autostart-Phase=Application
X-GNOME-Provides=login-sound
X-GNOME-Autostart-enabled=true

I installed sound-theme-freedesktop but the command > /usr/bin/canberra-gtk-play --id="desktop-login" --description="GNOME Login" doesn't work anymore.  
[QUOTE]Failed to play sound: File or data not found

Thanks in advance.

---

### Post by Dennis N on 2021-05-31
That all looks overly complex. I put my startup sound file + the script to run it in ~/.local/bin. The script file must be executable. I put a .desktop file to autorun the script in ~/.config/autostart. This setup works for me in Ubuntu Gnome.

---

### Post by dddman on 2021-05-31
I use the autostart file and it's quite fast at startup.  I did not know about local/bin; I guess its ok to create a bin directory if one does not exist.

My desktop entry file is similar to yours and located in ~/.config/autostart

> #!/usr/bin/env xdg-open
[Desktop Entry]
Type=Application
Exec=/usr/bin/focuswriter
Hidden=false
NoDisplay=false
X-GNOME-Autostart-enabled=true
Name[en_US]=FocusWriter
Name=FW
Comment[en_US]=autostart
Comment=autostart

I did have to point the gui at /usr/bin

[ATTACH=CONFIG]288585[/ATTACH]

---

