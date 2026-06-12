---
title: "Custom .desktop file doesn't show up in Synapse"
date: 2013-04-15
forum: General Help
---

### Post by Zvlwab on 2013-04-15
I have the following custom launcher:
```

remco@pc:~$ ls -l .local/share/applications/tuxguitar.desktop
-rwxrwxr-x 1 remco remco 457 Apr 11 22:58 .local/share/applications/tuxguitar.desktop
remco@pc:~$ cat .local/share/applications/tuxguitar.desktop 
./tuxguitar/tuxguitar-1_2-linux-x86-jcgo/bin-gtk-amd64/tuxguitar.sh
[Desktop Entry]
Version=1.2
Name=Tuxguitar
Comment=Edit, playback guitar tablatures
Exec=sh "/home/remco/.config/tuxguitar/tuxguitar-1_2-linux-x86-jcgo/bin-gtk-amd64/tuxguitar.sh"
Icon=/home/remco/.config/tuxguitar/tuxguitar-1_2-linux-x86-jcgo/classes/skins/Lavender/icon.ico
Terminal=false
Type=Application
Categories=AudioVideo;Audio;
MimeType=audio/x-tuxguitar;audio/x-gtp;audio/x-ptb;

```
It shows up correctly in the Xfce menu, but Synapse doesn't see it. Is anything wrong with this file?
After typing this question I noticed the first line myself. I have no idea how it got there, but I removed it and now it works

---

