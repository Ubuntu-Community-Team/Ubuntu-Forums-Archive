---
title: "weird XGL/beryl problem in dapper"
date: 2007-01-23
forum: General Help
---

### Post by darkenedday on 2007-01-23
I have just recently reinstalled dapper, on a machine that I have had 3d acceleration running on before, I tried the whole AIGLX thing but the modding i had to do to my xorg.conf file would not allow me to start x again and wouldn't even give me a command prompt to try and load my backup, So I tried running XGL again, I've had it before and it worked fine, I had it running on an old AMD duron 700mhz though and was rather laggy, I have recently upgraded this PC to a 1.2ghz AMD athlon thunderbird, and figured xgl shouldn't be too heavy of a load for it to carry

could it be that I dont have the correct kernel to match my proccessor? I believe that would be i686? if so would i have to completely reinstall my nvidia drivers? 

here is the output i get from running beryl --replace

mike@Apollo:~$ beryl --replace
XGL Absent, checking for NVIDIA
Nvidia Present
Relaunching beryl with __GL_YIELD="NOTHING"
XGL Absent, checking for NVIDIA
Nvidia Present
beryl: No composite extension


I have no idea what to do, I installed xgl witth the advice from a certain tutorial (the first one on the "one thread to rule them all v2 sticky) it had me add extra repos and install a package called xserver-xgl, from what i can find that is pretty much unanimous. . .

I have beryl running but there is no 3d acceleration. . .weird. . .HELP!

thanks in advance!

---

### Post by MoxJet on 2007-01-24
I have the same problem, any ideas?

---

### Post by azazel00 on 2007-01-24
Well, did you create the XGL session and log into it? If not, try the following. If yes, well, someone else should throw in their two cents.

```
$ sudo gedit /usr/local/bin/startxgl.sh
```

In gEdit, paste this:
```
#!/bin/sh
/usr/bin/Xgl :1 -fullscreen -ac -br -accel xv:fbo -accel glx:pbuffer &
sleep 4  
export DISPLAY=:1 
exec gnome-session
```

Then
```
$ sudo chmod a+x /usr/local/bin/startxgl.sh
$ sudo mkdir -p /etc/X11/sessions
$ sudo gedit /etc/X11/sessions/xgl.desktop
```

Paste the following:
```
[Desktop Entry]
Encoding=UTF-8
Name=Xgl
Exec=/usr/local/bin/startxgl.sh
Icon=
Type=Application
```

Restart, then when you are prompted for your login, click on "Session" and Choose the newly created XGL.

Note: I took this from [http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_XGL](http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_XGL)
It's for Edgy, but I dont see why it wouldnt work with Dapper since all the commands are for creating the Session and starting XGL. 

Hope it helps,
azazel

---

### Post by darkenedday on 2007-01-27
Ok so creating the session got xgl started  now have a new problem that's even harder for me to diagnose, it's not detecting my display i think. . . I'll paste the output. . . .

mike@Apollo:~$ beryl --replace
XGL Present
beryl: GLX_EXT_texture_from_pixmap is missing
beryl: Failed to manage screen: 0
beryl: No manageable screens found on display :1.0

i have no idea what to do form here, any inpt is appreciated

---

