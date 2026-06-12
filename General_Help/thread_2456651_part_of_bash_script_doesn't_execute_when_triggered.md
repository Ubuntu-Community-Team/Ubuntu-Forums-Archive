---
title: "part of bash script doesn't execute when triggered by udev rule"
date: 2021-01-16
forum: General Help
---

### Post by pidou66 on 2021-01-16
hello, 

I'm on Ubuntu 18.04.5 LTS and I wrote a script to take pictures and  send an email with ssmtp when someone removes a USB device from my  computer.
 the udev rule works fine and execute the script but only the "picture taking" part works, not the email sending.
 when I execute the script myself in a terminal, everything goes well,  the pictures are taken, the email is sent. It just doesn't work when it  is triggered by the udev rule.
 the rule:

```

 ACTION=="remove", SUBSYSTEM=="usb", RUN+="/home/jensen/Documents/script.sh"

```

 the script:

```


#!/bin/bash

cd /home/jensen
fswebcam -r 640x480 --jpeg 85 webcamshot1.jpg
fswebcam -r 640x480 --jpeg 85 webcamshot2.jpg
fswebcam -r 640x480 --jpeg 85 webcamshot3.jpg

echo "Subject: test mail" | /usr/sbin/sendmail -v [EMAIL="testmail@gmail.com"]testmail@gmail.com
[/EMAIL]
```

 and the ssmtp config:

```

root=**********@gmail.com
mailhub=smtp.gmail.com:587
hostname=jensen
AuthUser=**********@gmail.com
AuthPass=**********
UseSTARTTLS=yes
UseTLS=yes
FromLineOverride=yes 
```

 I tried changing the permissions on the script file with chmod but nothing works. what could be the issue ?

Another precision, I can create a new folder with my script with mkdir but if I try the following code, nothing happen ```
 "spd-say 'something' 
```

---

### Post by dinkidonk on 2021-01-16
These types of issues are almost always related to a missing environment or parts thereof. According to [this link]("http://www.postfix.org/sendmail.1.html") the sendmail command requires an environment variable which points to the location where the config file is located, so try to set it explicitly like this:

```
#!/bin/bash cd /home/jensen
fswebcam -r 640x480 --jpeg 85 webcamshot1.jpg
fswebcam -r 640x480 --jpeg 85 webcamshot2.jpg
fswebcam -r 640x480 --jpeg 85 webcamshot3.jpg

export MAIL_CONFIG=/path/to/config

echo "Subject: test mail" | /usr/sbin/sendmail -v [EMAIL="testmail@gmail.com"]testmail@gmail.com[/EMAIL]
```

---

### Post by pidou66 on 2021-01-16
yes but why would it work fine when I execute it myself via a terminal ?
what is the difference between executing the script myself and a rule executing it ?

---

### Post by dinkidonk on 2021-01-16
Because the terminal is run with a full environment, you can try to put this in the script:

```
env > /home/jensen/env.txt
```

And check if there is any difference in the environment from the console and the udev rule.

---

### Post by pidou66 on 2021-01-16
I juste edited my last reply, I didn't understood the use of the line you sent me at first. here are the results :

env.txt when the usb device is removed:

```
ACTION=remove
USEC_INITIALIZED=7702106033
SUBSYSTEM=usb
SEQNUM=3463
BUSNUM=002
TYPE=0/0/0
DEVPATH=/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.1
PWD=/
MINOR=141
DEVTYPE=usb_device
MAJOR=189
DEVNAME=/dev/bus/usb/002/014
SHLVL=1
PRODUCT=46d/c077/7200
DEVNUM=014
_=/usr/bin/env


```

env.txt when I execute the code in a terminal :

```
CLUTTER_IM_MODULE=xim
LS_COLORS=rs=0:di=01;34:ln=01;36:mh=00:pi=40;33:so=01;35:do=01;35:bd=40;33;01:cd=40;33;01:or=40;31;01:mi=00:su=37;41:sg=30;43:ca=30;41:tw=30;42:ow=34;42:st=37;44:ex=01;32:*.tar=01;31:*.tgz=01;31:*.arc=01;31:*.arj=01;31:*.taz=01;31:*.lha=01;31:*.lz4=01;31:*.lzh=01;31:*.lzma=01;31:*.tlz=01;31:*.txz=01;31:*.tzo=01;31:*.t7z=01;31:*.zip=01;31:*.z=01;31:*.Z=01;31:*.dz=01;31:*.gz=01;31:*.lrz=01;31:*.lz=01;31:*.lzo=01;31:*.xz=01;31:*.zst=01;31:*.tzst=01;31:*.bz2=01;31:*.bz=01;31:*.tbz=01;31:*.tbz2=01;31:*.tz=01;31:*.deb=01;31:*.rpm=01;31:*.jar=01;31:*.war=01;31:*.ear=01;31:*.sar=01;31:*.rar=01;31:*.alz=01;31:*.ace=01;31:*.zoo=01;31:*.cpio=01;31:*.7z=01;31:*.rz=01;31:*.cab=01;31:*.wim=01;31:*.swm=01;31:*.dwm=01;31:*.esd=01;31:*.jpg=01;35:*.jpeg=01;35:*.mjpg=01;35:*.mjpeg=01;35:*.gif=01;35:*.bmp=01;35:*.pbm=01;35:*.pgm=01;35:*.ppm=01;35:*.tga=01;35:*.xbm=01;35:*.xpm=01;35:*.tif=01;35:*.tiff=01;35:*.png=01;35:*.svg=01;35:*.svgz=01;35:*.mng=01;35:*.pcx=01;35:*.mov=01;35:*.mpg=01;35:*.mpeg=01;35:*.m2v=01;35:*.mkv=01;35:*.webm=01;35:*.ogm=01;35:*.mp4=01;35:*.m4v=01;35:*.mp4v=01;35:*.vob=01;35:*.qt=01;35:*.nuv=01;35:*.wmv=01;35:*.asf=01;35:*.rm=01;35:*.rmvb=01;35:*.flc=01;35:*.avi=01;35:*.fli=01;35:*.flv=01;35:*.gl=01;35:*.dl=01;35:*.xcf=01;35:*.xwd=01;35:*.yuv=01;35:*.cgm=01;35:*.emf=01;35:*.ogv=01;35:*.ogx=01;35:*.aac=00;36:*.au=00;36:*.flac=00;36:*.m4a=00;36:*.mid=00;36:*.midi=00;36:*.mka=00;36:*.mp3=00;36:*.mpc=00;36:*.ogg=00;36:*.ra=00;36:*.wav=00;36:*.oga=00;36:*.opus=00;36:*.spx=00;36:*.xspf=00;36:
LC_MEASUREMENT=fr_FR.UTF-8
LESSCLOSE=/usr/bin/lesspipe %s %s
LC_PAPER=fr_FR.UTF-8
LC_MONETARY=fr_FR.UTF-8
TERMINATOR_UUID=urn:uuid:9462136c-4e92-4fe1-b0cd-c81922e89d14
XDG_MENU_PREFIX=gnome-
_=/usr/bin/env
LANG=en_US.UTF-8
DISPLAY=:0
OLDPWD=/home/jensen
GNOME_SHELL_SESSION_MODE=ubuntu
COLORTERM=truecolor
USERNAME=jensen
XDG_VTNR=2
GIO_LAUNCHED_DESKTOP_FILE_PID=2324
SSH_AUTH_SOCK=/run/user/1000/keyring/ssh
LC_NAME=fr_FR.UTF-8
XDG_SESSION_ID=2
USER=jensen
DESKTOP_SESSION=ubuntu
QT4_IM_MODULE=xim
TEXTDOMAINDIR=/usr/share/locale/
PWD=/home/jensen/Documents
HOME=/home/jensen
TEXTDOMAIN=im-config
SSH_AGENT_PID=1697
QT_ACCESSIBILITY=1
XDG_SESSION_TYPE=x11
XDG_DATA_DIRS=/usr/share/ubuntu:/usr/local/share/:/usr/share/:/var/lib/snapd/desktop
TERMINATOR_DBUS_NAME=net.tenshu.Terminator20x1a6021154d881c
XDG_SESSION_DESKTOP=ubuntu
LC_ADDRESS=fr_FR.UTF-8
GJS_DEBUG_OUTPUT=stderr
LC_NUMERIC=fr_FR.UTF-8
GTK_MODULES=gail:atk-bridge
TERMINATOR_DBUS_PATH=/net/tenshu/Terminator2
WINDOWPATH=2
SHELL=/bin/bash
VTE_VERSION=5202
TERM=xterm-256color
QT_IM_MODULE=xim
XMODIFIERS=@im=ibus
IM_CONFIG_PHASE=2
XDG_CURRENT_DESKTOP=ubuntu:GNOME
GPG_AGENT_INFO=/run/user/1000/gnupg/S.gpg-agent:0:1
GIO_LAUNCHED_DESKTOP_FILE=/usr/share/applications/terminator.desktop
SHLVL=2
XDG_SEAT=seat0
LC_TELEPHONE=fr_FR.UTF-8
GDMSESSION=ubuntu
GNOME_DESKTOP_SESSION_ID=this-is-deprecated
LOGNAME=jensen
DBUS_SESSION_BUS_ADDRESS=unix:path=/run/user/1000/bus
XDG_RUNTIME_DIR=/run/user/1000
XAUTHORITY=/run/user/1000/gdm/Xauthority
XDG_CONFIG_DIRS=/etc/xdg/xdg-ubuntu:/etc/xdg
PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games:/snap/bin
LC_IDENTIFICATION=fr_FR.UTF-8
GJS_DEBUG_TOPICS=JS ERROR;JS LOG
SESSION_MANAGER=local/jensen-Aspire-E1-531:@/tmp/.ICE-unix/1602,unix/jensen-Aspire-E1-531:/tmp/.ICE-unix/1602
LESSOPEN=| /usr/bin/lesspipe %s
GTK_IM_MODULE=ibus
LC_TIME=fr_FR.UTF-8
```

---

### Post by dinkidonk on 2021-01-16
There is a big difference in the two environments, so now you know why there is a difference from inside the terminal and outside. Try to change the permissions of the script so it belongs to root. If that does nothing, try to run the script as your user by changing the udev rule to use "su" to change user:

```
ACTION=="remove", SUBSYSTEM=="usb", RUN+="/bin/su jensen -c '/home/jensen/Documents/script.sh'"
```

---

### Post by pidou66 on 2021-01-16
I just edited my rule with " /bin/su jensen -c '/home/jensen/Documents/script.sh' "and it works perfectly, thank you so much !

---

