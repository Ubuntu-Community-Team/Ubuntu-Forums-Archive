---
title: "VLC doesn't show up with LXDE on Ubuntu 18.04.01"
date: 2018-11-19
forum: General Help
---

### Post by galacticstone on 2018-11-19
Hi Folks,

I switched over to LXDE for a lighter desktop (I don't use many of Gnome's bells and whistles), and my installation of VLC does not show up anywhere. I can run it from the command line, but it doesn't show up under the program menu or the supported programs to open media. How can I make LXDE see VLC?

Thanks!

MikeG

---

### Post by ajgreeny on 2018-11-19
There should be a **vlc.desktop** file in **/usr/share/applications** which you could copy to **/home/username/.local/share/applications** and if necessary you can then edit it to ensure it shows in the Sound and Video multimedia section of your menu.

You could also copy the text below, save it as **vlc.desktop** and move  it into **~/.local/share/applications** when it should appear in your menu and work fine.
```
[Desktop Entry]
Version=1.0
Name=VLC media player
GenericName=Media player
Exec=/usr/bin/vlc --started-from-file %U
TryExec=/usr/bin/vlc
Icon=vlc
Terminal=false
Type=Application
Categories=AudioVideo;Player;Recorder;
Keywords=Player;Capture;DVD;Audio;Video;Server;Broadcast;

```

---

