---
title: "lack of system sounds"
date: 2015-01-29
forum: General Help
---

### Post by kris34 on 2015-01-29
Xubuntu 14.10 64 bit

I don't see any system sounds.
I cannot find any solution on internet, any suggestions ?

$ xfconf-query -c xsettings -p /Net/SoundThemeName
default

$ ls -l /usr/share/sounds/$(xfconf-query -c xsettings -p /Net/SoundThemeName)
8
-rw-r--r-- 1 root root   85 sty 29 18:03 index.theme
drwxr-xr-x 2 root root 4096 sty 29 18:03 stereo

$ xfconf-query -c xsettings -p /Net/EnableInputFeedbackSounds
true

$ echo $GTK_MODULES
empty

$ cat /etc/X11/Xsession.d/52libcanberra-gtk-module_add-to-gtk-modules 

no file / directory "52libcanberra-gtk-module_add-to-gtk-modules"

---

### Post by Toz on 2015-01-31
Have you tried [these]("http://ubuntuforums.org/showthread.php?t=2156763&p=12702910&viewfull=1#post12702910") instructions? You need to create the /etc/X11/Xsession.d/52libcanberra-gtk-module_add-to-gtk-modules file. 

Other links:
- [http://ubuntuforums.org/showthread.php?t=2209372]("http://ubuntuforums.org/showthread.php?t=2209372")
- [http://ubuntuforums.org/showthread.php?t=2219786]("http://ubuntuforums.org/showthread.php?t=2219786")
- [https://forum.xfce.org/viewtopic.php?id=8618]("https://forum.xfce.org/viewtopic.php?id=8618")

---

### Post by kris34 on 2015-02-02
It helps me. In this moment I have not only start/login GUI or logout sounds.

---

### Post by Toz on 2015-02-02
For the login sound, add the following command to Settings Manager >> Session and Startup >> Application Autostart:
```
aplay /path/to/login/sound
```
...and change "/path/to/login/sound" to the actual path and file name of a login sound.

---

For logout sound, you need interrupt xfce4-session. To do so, with root privlidges, create the file **/usr/local/bin/xfce4-session** with the following content:
```
#!/bin/bash

# run the real xfce4-session executable
/usr/bin/xfce4-session

# on exit, run my stuff
aplay /path/to/logout/sound
```
...and change "/path/to/logout/sound" to be the path and filename to your logout sound. Also, remember to make this file executable:
```
sudo chmod +x /usr/local/bin/xfce4-session
```

---

### Post by kris34 on 2015-02-02
Thank you.


I see this is really big difference between Win an Linux/Ubuntu .
Still questions, workaround solutions, and so on

No wonder people decide on Windows instead of Linux !

 
[FONT=Calibri][SIZE=3] 
[FONT=Calibri][SIZE=3] 
[/SIZE][/FONT][/SIZE][/FONT]

---

### Post by raptir on 2015-02-02
> **kris34 said:**
> Thank you.


I see this is really big difference between Win an Linux/Ubuntu .
Still questions, workaround solutions, and so on

No wonder people decide on Windows instead of Linux !

 
[FONT=Calibri][SIZE=3] 
[FONT=Calibri][SIZE=3] 
[/SIZE][/FONT][/SIZE][/FONT]

Really? You think people decide on Windows because it's easier to get a ding to play when you login/logout?

---

### Post by kris34 on 2015-02-02
of course it is the one small example :-\"

---

### Post by QIII on 2015-02-02
Xubuntu does not have system sounds be default.  That is the choice of the developers.  Other flavors of Ubuntu and other distros do.

Xubuntu is a Linux-based OS, but not all Linux is Xubuntu.

---

### Post by kris34 on 2015-02-02
Light distro or advanced one . I see !
Thx.

---

### Post by raptir on 2015-02-02
It's not necessarily that Xfce isn't advanced, but it is meant to be light. They include advanced functionality that adds to usability (for example, compositing). System sounds are more "flourishes" than functionality, so they are excluded.

---

### Post by kris34 on 2015-02-03
> **Toz said:**
> 
```
aplay /path/to/login/sound
```


Unfortunately aplay file.ogg produce noise instead of sound.

---

### Post by Toz on 2015-02-03
aplay does not play ogg files. Try:
```
canberra-gtk-play -f file.ogg
```

---

### Post by kris34 on 2015-02-04
I don't have [COLOR=#000000][FONT=Ubuntu Mono]canberra-gtk-play in [/FONT][/COLOR]my xubuntu [FONT=Ubuntu Mono, monospace][COLOR=#000000]but the system sounds play OK[/COLOR][/FONT]
[FONT=Ubuntu Mono, monospace][COLOR=#000000]
Linux is probably not for average users I think.[/COLOR][/FONT]

---

### Post by Toz on 2015-02-04
> **kris34 said:**
> I don't have canberra-gtk-play in my xubuntu but the system sounds play OK
canberra-gtk-play is part of the **gnome-session-canberra** package - make sure you have it installed.
> Linux is probably not for average users I think.
That is a matter of opinion. Linux is less suitable for some people more than others. At the end of the day, you should use whatever operating system you are most productive and comfortable with.

---

### Post by kris34 on 2015-02-04
Thank you

---

