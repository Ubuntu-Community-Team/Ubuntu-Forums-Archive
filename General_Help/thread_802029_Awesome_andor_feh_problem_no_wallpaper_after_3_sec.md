---
title: "Awesome and/or feh problem: no wallpaper after 3 seconds"
date: 2008-05-21
forum: General Help
---

### Post by red_Marvin on 2008-05-21
Former title: Awesome and/or feh problem: no wallpaper after 3 seconds

I have an odd problem, when I log in awesome is started, and I have a script use feh to set my wallpaper, however, for a few weeks now I've had a problem: After a few seconds the wallpaper is set to gray and I have to manually execute *sh .fehbg* to get it back. Is something drawn on top of it?
```
**leo@snow:~$ cat /usr/share/xsessions/awesome.desktop**
[Desktop Entry]
Encoding=UTF-8
Name=Awesome
Comment=Log in using the Awesome window manager
Exec=/home/leo/.awesome.sh
Icon=
Type=Application

**leo@snow:~$ cat .awesome.sh**
#!/bin/bash
#AUTOSTARTED APPS AND SETTINGS

#STATUSBAR TEXT

#Launch awesome
exec gnome-settings-daemon &
exec python /home/leo/.awesome/baroffoo.py &
exec sh "/home/leo/.wacomsettings" &
exec sh "/home/leo/.fehbg" &
sleep 1 && exec awesome

**leo@snow:~$ cat .fehbg**
feh --bg-tile "/home/leo/media/bilder/hdr/scaledpipes.jpg"

```

Note that .fehbg sucsesfully sets the wallpaper, so it's not a path error, but it gets overdrawn later it seems. No trace is left in dmesg.

---

### Post by red_Marvin on 2008-05-23
I found the reason and solution to the problem, and I post it here so if anybody else has this problem (or a similar one since the reasons are fairly generic) they can hopefully find this and solve it.
Thread title will be changed to reflect the problem better.


For some reason, possibly an update, gnome-settings-daemon decided to start caring about the background too, and since my wall in gnome is/was gray at the time I switched to awesome that, was what it put on my screen.

Solution:
Run gnome-appearance-properties and set your wallpaper to what you want.
I still kept the exec sh "/home/leo.fehbg" & line in my .awesome.sh script
since it loads the wallpaper earlier.

---

