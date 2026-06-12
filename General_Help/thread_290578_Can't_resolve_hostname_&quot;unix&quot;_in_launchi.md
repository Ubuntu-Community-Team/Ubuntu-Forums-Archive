---
title: "Can't resolve hostname &quot;unix&quot; in launching gnome apps"
date: 2006-11-01
forum: General Help
---

### Post by ricp on 2006-11-01
Hello,

i have an ubuntu desktop distrib 6.06, i have an irritating :-k  when i start some gnome applications :

xxxx@sd-xxxx:/usr/bin$ gnome-search-tool
Can't resolve host name "unix"!
xxxx@sd-xxxx:/usr/bin$ gedit
Can't resolve host name "unix"!
xxxx@sd-xxxx:/usr/bin$ gnome-mouse-properties

some other apps don't like gnome-terminal for example. The problem is machine's hostname and ips in /etc/hosts have nothing to do with "unix" name. Don't know if it helps but DISPLAY en var is set to "unix:1000.0" and i use a nx client to access the desktop.

Any ideas on this and where this apps could take this name "unix" i didn't find anywhere?

Thank u,

Ric

---

### Post by taurus on 2006-11-01
Well, what exactly does your /etc/hosts look like then???

---

### Post by ricp on 2006-11-01
yes, here it is. my host file where sd-yyyy is what i get with hostname and xxx my ip adress:

# 'hosts' file configuration.

127.0.0.1       sd-yyyy.local   localhost
xx.xxx.xx.xxx   sd-yyyy sd-yyyy

---

### Post by bettlebrox on 2006-11-01
what is the output of env ? (There maybe some output there you not want anyone to see so maybe edit it before posting).

A quick hack, might be to add unix to the first line of your /etc/hosts, like so:

127.0.0.1 localhost.localdomain localhost mylaptop unix

---

### Post by ricp on 2006-11-01
Here it is after env:

TERM=xterm
DESKTOP_STARTUP_ID=
SHELL=/bin/bash
SSH_CLIENT=127.0.0.1 55917 22
GTK_RC_FILES=/etc/gtk/gtkrc:/home/xxxxxxx/.gtkrc-1.2-gnome2
WINDOWID=27263067
USER=xxxxxxxx
LS_COLORS=no=00:fi=00:di=01;34:ln=01;36:pi=40;33:so=01;35:do=01;35:bd=40;33;01:cd=40;33;01:or=40;31;01:su=37;41:sg=30;43:tw=30;42:ow=34;42:st=37;44:ex=01;32:*.tar=01;31:*.tgz=01;31:*.arj=01;31:*.taz=01;31:*.lzh=01;31:*.zip=01;31:*.z=01;31:*.Z=01;31:*.gz=01;31:*.bz2=01;31:*.deb=01;31:*.rpm=01;31:*.jar=01;31:*.jpg=01;35:*.jpeg=01;35:*.gif=01;35:*.bmp=01;35:*.pbm=01;35:*.pgm=01;35:*.ppm=01;35:*.tga=01;35:*.xbm=01;35:*.xpm=01;35:*.tif=01;35:*.tiff=01;35:*.png=01;35:*.mov=01;35:*.mpg=01;35:*.mpeg=01;35:*.avi=01;35:*.fli=01;35:*.gl=01;35:*.dl=01;35:*.xcf=01;35:*.xwd=01;35:*.flac=01;35:*.mp3=01;35:*.mpc=01;35:*.ogg=01;35:*.wav=01;35:
GNOME_KEYRING_SOCKET=/tmp/keyring-LGh2Aq/socket
SESSION_MANAGER=local/sd-yyyy:/tmp/.ICE-unix/4321
MAIL=/var/mail/xxxxxxxxxx
PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11:/usr/games
PWD=xxxxxxx
LANG=fr_FR.UTF-8
HISTCONTROL=ignoredups
SHLVL=3
HOME=/home/xxxxxx
LANGUAGE=fr_FR:fr:en_GB:en
GNOME_DESKTOP_SESSION_ID=Default
LOGNAME=xxxxxxx
SSH_CONNECTION=127.0.0.1 55917 127.0.0.1 22
LESSOPEN=| /usr/bin/lesspipe %s
DISPLAY=unix:1000.0
LESSCLOSE=/usr/bin/lesspipe %s %s
COLORTERM=gnome-terminal
_=/usr/bin/env

Sure i could try to put unix in hosts...  but there might be something wrong that i m not aware of. Thanks for your responses....

ricp

---

### Post by fragos on 2006-11-02
Your system's hostname is stored in text file /etc/hostname.  That is the name that's used to access access your PC from others.

---

