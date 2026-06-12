---
title: "Can't run script in folder listed on $PATH"
date: 2018-03-26
forum: General Help
---

### Post by boydya on 2018-03-26
Sorry if this is obvious but I am banging my head on the wall here!

I am trying to run a test script in /usr/local/cuda-9.1/bin/test.sh

When I type in env I get the following for PATH.
```

XDG_VTNR=7
XDG_SESSION_ID=c4
CLUTTER_IM_MODULE=xim
XDG_GREETER_DATA_DIR=/var/lib/lightdm-data/dag0r
GPG_AGENT_INFO=/home/dag0r/.gnupg/S.gpg-agent:0:1
SHELL=/bin/bash
TERM=xterm-256color
VTE_VERSION=4205
QT_LINUX_ACCESSIBILITY_ALWAYS_ON=1
WINDOWID=52428810
UPSTART_SESSION=unix:abstract=/com/ubuntu/upstart-session/1000/6065
GNOME_KEYRING_CONTROL=
GTK_MODULES=gail:atk-bridge:unity-gtk-module
USER=dag0r
LS_COLORS=rs=0:di=01;34:ln=01;36:mh=00:pi=40;33:so=01;35:do=01;35:bd=40;33;01:cd=40;33;01:or=40;31;01:mi=00:su=37;41:sg=30;43:ca=30;41:tw=30;42:ow=34;42:st=37;44:ex=01;32:*.tar=01;31:*.tgz=01;31:*.arc=01;31:*.arj=01;31:*.taz=01;31:*.lha=01;31:*.lz4=01;31:*.lzh=01;31:*.lzma=01;31:*.tlz=01;31:*.txz=01;31:*.tzo=01;31:*.t7z=01;31:*.zip=01;31:*.z=01;31:*.Z=01;31:*.dz=01;31:*.gz=01;31:*.lrz=01;31:*.lz=01;31:*.lzo=01;31:*.xz=01;31:*.bz2=01;31:*.bz=01;31:*.tbz=01;31:*.tbz2=01;31:*.tz=01;31:*.deb=01;31:*.rpm=01;31:*.jar=01;31:*.war=01;31:*.ear=01;31:*.sar=01;31:*.rar=01;31:*.alz=01;31:*.ace=01;31:*.zoo=01;31:*.cpio=01;31:*.7z=01;31:*.rz=01;31:*.cab=01;31:*.jpg=01;35:*.jpeg=01;35:*.gif=01;35:*.bmp=01;35:*.pbm=01;35:*.pgm=01;35:*.ppm=01;35:*.tga=01;35:*.xbm=01;35:*.xpm=01;35:*.tif=01;35:*.tiff=01;35:*.png=01;35:*.svg=01;35:*.svgz=01;35:*.mng=01;35:*.pcx=01;35:*.mov=01;35:*.mpg=01;35:*.mpeg=01;35:*.m2v=01;35:*.mkv=01;35:*.webm=01;35:*.ogm=01;35:*.mp4=01;35:*.m4v=01;35:*.mp4v=01;35:*.vob=01;35:*.qt=01;35:*.nuv=01;35:*.wmv=01;35:*.asf=01;35:*.rm=01;35:*.rmvb=01;35:*.flc=01;35:*.avi=01;35:*.fli=01;35:*.flv=01;35:*.gl=01;35:*.dl=01;35:*.xcf=01;35:*.xwd=01;35:*.yuv=01;35:*.cgm=01;35:*.emf=01;35:*.ogv=01;35:*.ogx=01;35:*.aac=00;36:*.au=00;36:*.flac=00;36:*.m4a=00;36:*.mid=00;36:*.midi=00;36:*.mka=00;36:*.mp3=00;36:*.mpc=00;36:*.ogg=00;36:*.ra=00;36:*.wav=00;36:*.oga=00;36:*.opus=00;36:*.spx=00;36:*.xspf=00;36:
QT_ACCESSIBILITY=1
LD_LIBRARY_PATH=/usr/local/cuda-9.1/lib64${LD_LIBRARY_PATH:+
XDG_SESSION_PATH=/org/freedesktop/DisplayManager/Session1
XDG_SEAT_PATH=/org/freedesktop/DisplayManager/Seat0
SSH_AUTH_SOCK=/run/user/1000/keyring/ssh
DEFAULTS_PATH=/usr/share/gconf/ubuntu.default.path
XDG_CONFIG_DIRS=/etc/xdg/xdg-ubuntu:/usr/share/upstart/xdg:/etc/xdg
PATH=/home/dag0r/bin:/home/dag0r/anaconda2/bin:/usr/local/cuda-9.1/bin:/home/dag0r/bin:/home/dag0r/.local/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games:/snap/bin
DESKTOP_SESSION=ubuntu
QT_IM_MODULE=ibus
QT_QPA_PLATFORMTHEME=appmenu-qt5
XDG_SESSION_TYPE=x11
PWD=/home/dag0r
JOB=gnome-session
XMODIFIERS=@im=ibus
GNOME_KEYRING_PID=
LANG=en_GB.UTF-8
GDM_LANG=en_GB
MANDATORY_PATH=/usr/share/gconf/ubuntu.mandatory.path
IM_CONFIG_PHASE=1
COMPIZ_CONFIG_PROFILE=ubuntu
GDMSESSION=ubuntu
SESSIONTYPE=gnome-session
GTK2_MODULES=overlay-scrollbar
HOME=/home/dag0r
XDG_SEAT=seat0
SHLVL=1
LANGUAGE=en_GB:en
GNOME_DESKTOP_SESSION_ID=this-is-deprecated
UPSTART_INSTANCE=
UPSTART_EVENTS=started starting
XDG_SESSION_DESKTOP=ubuntu
LOGNAME=dag0r
QT4_IM_MODULE=xim
XDG_DATA_DIRS=/usr/share/ubuntu:/usr/share/gnome:/usr/local/share:/usr/share:/var/lib/snapd/desktop:/var/lib/snapd/desktop
DBUS_SESSION_BUS_ADDRESS=unix:abstract=/tmp/dbus-8bqAfPqXAf
LESSOPEN=| /usr/bin/lesspipe %s
INSTANCE=Unity
UPSTART_JOB=unity-settings-daemon
XDG_RUNTIME_DIR=/run/user/1000
DISPLAY=:0
XDG_CURRENT_DESKTOP=Unity
GTK_IM_MODULE=ibus
LESSCLOSE=/usr/bin/lesspipe %s %s
XAUTHORITY=/home/dag0r/.Xauthority
_=/usr/bin/env
```

The command I am using to run the script is ```
sudo sh test.sh
```. If I run the script locally it executes successfully. Is there anything obviously wrong with my PATH?

I use the following line in .profile to add CUDA to PATH

```
export PATH=/usr/local/cuda-9.1/bin${PATH:+:${PATH}}
```

Any help appreciated!

---

### Post by spjackson on 2018-03-26
Welcome to the forums.

> **boydya said:**
> 

I use the following line in .profile to add CUDA to PATH

```
export PATH=/usr/local/cuda-9.1/bin${PATH:+:${PATH}}
```


When you run sudo a different PATH takes effect as you will see with:
```

sudo env | fgrep PATH

```
sudo's PATH is set as secure_path in /etc/sudoers. It is not recommended to change this.

But also:
> **boydya said:**
> 
```
sudo sh test.sh
```

The PATH environment variable controls where the shell looks for commands. It does not have any effect on how the *sh *command searches for its first parameter.
```

sudo test.sh

```
would search sudo's PATH for test.sh, but 
```
sudo sh test.sh
```
would not. (It just searches sudo's PATH for sh, not for test.sh.) Is there a reason why you can't do one of the following?
```

sudo /usr/local/cuda-9.1/bin/test.sh
# or
sudo sh /usr/local/cuda-9.1/bin/test.sh

```

---

### Post by boydya on 2018-03-26
Hi spjackson

Yeah that did it. TBH I thought I needed to be able to access via PATH for CUDA to work, but the samples seem to compile now so all good. 

So the path as root is different. Won't forget that in a hurry!

Thanks!

---

