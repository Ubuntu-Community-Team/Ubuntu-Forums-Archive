---
title: "What cron env variable do I need to set for gnome's notify-send?"
date: 2018-01-01
forum: General Help
---

### Post by again? on 2018-01-01
Ubuntu 17.04, Gnome desktop.

I have a cron job that works...
```
* * * * * /home/glen/scripts/notify-test.sh
```

I had to set the  env $DISPLAY variable for the notify-send command to work.
```
#!/bin/bash
export DISPLAY=:1
notify-send -i info "Crontest"
```

But I also have an xfce session installed and notify-send is using xfce4-notifyd to display messages instead of gnome's notification.
What env variable do I need to set so the cron job uses gnome's notification display.
```
glen@GU17:~$ env
CLUTTER_IM_MODULE=xim
LS_COLORS=rs=0:di=01;34:ln=01;36:mh=00:pi=40;33:so=01;35:do=01;35:bd=40;33;01:cd=40;33;01:or=40;31;01:mi=00:su=37;41:sg=30;43:ca=30;41:tw=30;42:ow=34;42:st=37;44:ex=01;32:*.tar=01;31:*.tgz=01;31:*.arc=01;31:*.arj=01;31:*.taz=01;31:*.lha=01;31:*.lz4=01;31:*.lzh=01;31:*.lzma=01;31:*.tlz=01;31:*.txz=01;31:*.tzo=01;31:*.t7z=01;31:*.zip=01;31:*.z=01;31:*.Z=01;31:*.dz=01;31:*.gz=01;31:*.lrz=01;31:*.lz=01;31:*.lzo=01;31:*.xz=01;31:*.zst=01;31:*.tzst=01;31:*.bz2=01;31:*.bz=01;31:*.tbz=01;31:*.tbz2=01;31:*.tz=01;31:*.deb=01;31:*.rpm=01;31:*.jar=01;31:*.war=01;31:*.ear=01;31:*.sar=01;31:*.rar=01;31:*.alz=01;31:*.ace=01;31:*.zoo=01;31:*.cpio=01;31:*.7z=01;31:*.rz=01;31:*.cab=01;31:*.jpg=01;35:*.jpeg=01;35:*.mjpg=01;35:*.mjpeg=01;35:*.gif=01;35:*.bmp=01;35:*.pbm=01;35:*.pgm=01;35:*.ppm=01;35:*.tga=01;35:*.xbm=01;35:*.xpm=01;35:*.tif=01;35:*.tiff=01;35:*.png=01;35:*.svg=01;35:*.svgz=01;35:*.mng=01;35:*.pcx=01;35:*.mov=01;35:*.mpg=01;35:*.mpeg=01;35:*.m2v=01;35:*.mkv=01;35:*.webm=01;35:*.ogm=01;35:*.mp4=01;35:*.m4v=01;35:*.mp4v=01;35:*.vob=01;35:*.qt=01;35:*.nuv=01;35:*.wmv=01;35:*.asf=01;35:*.rm=01;35:*.rmvb=01;35:*.flc=01;35:*.avi=01;35:*.fli=01;35:*.flv=01;35:*.gl=01;35:*.dl=01;35:*.xcf=01;35:*.xwd=01;35:*.yuv=01;35:*.cgm=01;35:*.emf=01;35:*.ogv=01;35:*.ogx=01;35:*.aac=00;36:*.au=00;36:*.flac=00;36:*.m4a=00;36:*.mid=00;36:*.midi=00;36:*.mka=00;36:*.mp3=00;36:*.mpc=00;36:*.ogg=00;36:*.ra=00;36:*.wav=00;36:*.oga=00;36:*.opus=00;36:*.spx=00;36:*.xspf=00;36:
LESSCLOSE=/usr/bin/lesspipe %s %s
XDG_MENU_PREFIX=gnome-
LANG=en_AU.UTF-8
DISPLAY=:1
QT_STYLE_OVERRIDE=
GTK_OVERLAY_SCROLLING=0
COLORTERM=altyo
USERNAME=glen
JAVA_HOME=/usr/lib/jvm/java-9-oracle
J2SDKDIR=/usr/lib/jvm/java-9-oracle
XDG_VTNR=2
GIO_LAUNCHED_DESKTOP_FILE_PID=2773
SSH_AUTH_SOCK=/run/user/1000/keyring/ssh
MANDATORY_PATH=/usr/share/gconf/gnome.mandatory.path
XDG_SESSION_ID=3
DERBY_HOME=/usr/lib/jvm/java-9-oracle/db
USER=glen
DESKTOP_SESSION=gnome
QT4_IM_MODULE=xim
DEFAULTS_PATH=/usr/share/gconf/gnome.default.path
QT_QPA_PLATFORMTHEME=gtk2
PWD=/home/glen
HOME=/home/glen
JOURNAL_STREAM=8:26506
J2REDIR=/usr/lib/jvm/java-9-oracle
SSH_AGENT_PID=2495
QT_ACCESSIBILITY=1
XDG_SESSION_TYPE=x11
XDG_DATA_DIRS=/usr/share/gnome:/usr/local/share:/usr/share:/var/lib/snapd/desktop:/var/lib/snapd/desktop
XDG_SESSION_DESKTOP=gnome
GTK_MODULES=:topmenu-gtk-module:gail:atk-bridge
WINDOWPATH=2
TERM=xterm
SHELL=/bin/bash
QT_IM_MODULE=ibus
XMODIFIERS=@im=ibus
XDG_CURRENT_DESKTOP=GNOME
QT_LINUX_ACCESSIBILITY_ALWAYS_ON=1
GIO_LAUNCHED_DESKTOP_FILE=/home/glen/.config/autostart/org.gtk.altyo.desktop
SHLVL=1
XDG_SEAT=seat0
LANGUAGE=en_AU:en
PROMPT_COMMAND=history -a; history -c; history -r; preexec_set_exit;preexec_invoke_cmd
GDMSESSION=gnome
GNOME_DESKTOP_SESSION_ID=this-is-deprecated
LOGNAME=glen
DBUS_SESSION_BUS_ADDRESS=unix:path=/run/user/1000/bus
XDG_RUNTIME_DIR=/run/user/1000
XAUTHORITY=/run/user/1000/gdm/Xauthority
XDG_CONFIG_DIRS=/etc/xdg/xdg-gnome:/etc/xdg
PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games:/home/glen/.local/bin:/home/glen/bin
XDG_SESSION_COOKIE=a18c05480c0340f7bd2697ab86115e62-1514853758.377668-955710324
SESSION_MANAGER=local/GU17:@/tmp/.ICE-unix/2366,unix/GU17:/tmp/.ICE-unix/2366
LESSOPEN=| /usr/bin/lesspipe %s
GTK_IM_MODULE=ibus
_=/usr/bin/env
```

I tried "**export DESKTOP_SESSION=gnome**" but no luck.

---

### Post by again? on 2018-01-02
After some trial and error turns out to be dbus.
ie
```
export DBUS_SESSION_BUS_ADDRESS=unix:path=/run/user/1000/bus
```

---

