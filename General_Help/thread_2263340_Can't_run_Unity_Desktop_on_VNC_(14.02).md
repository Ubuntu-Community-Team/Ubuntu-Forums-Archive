---
title: "Can't run Unity Desktop on VNC (14.02)"
date: 2015-01-31
forum: General Help
---

### Post by przemek7 on 2015-01-31
I am trying to run unity desktop on my server. I have to connect via the VNC. All I see after connecting with the VNC is terminal on the grey background, nothing else. This is my vnc4server configuration file:

```

#!/bin/sh

# Uncomment the following two lines for normal desktop:
# unset SESSION_MANAGER
# exec /etc/X11/xinit/xinitrc

[ -x /etc/vnc/xstartup ] && exec /etc/vnc/xstartup
[ -r $HOME/.Xresources ] && xrdb $HOME/.Xresources
xsetroot -solid grey
vncconfig -iconic &
x-terminal-emulator -geometry 80x24+10+10 -ls -title "$VNCDESKTOP Desktop" &
x-window-manager &

```

I tried "startx" and nothing happenned.

---

### Post by przemek7 on 2015-01-31
Let's start from the beginning. I did this:

 If you would like to create startup entries
  ```
$ cd ~
$ > .vnc/xstartup
$ nano .vnc/xstartup

```  paste:
  ```
#!/bin/sh
unset SESSION_MANAGER
unset DBUS_SESSION_BUS_ADDRESS
startxfce4 &

[ -x /etc/vnc/xstartup ] && exec /etc/vnc/xstartup
[ -r $HOME/.Xresources ] && xrdb $HOME/.Xresources
xsetroot -solid grey
vncconfig -iconic &

```  Create VNC Server statup script.
  sudo nano /etc/init.d/vncserver
  paste:
  ```
#!/bin/bash
unset VNCSERVERARGS
VNCSERVERS=""
[ -f /etc/vncserver/vncservers.conf ] && . /etc/vncserver/vncservers.conf
prog=$"VNC server"
start() {
 . /lib/lsb/init-functions
 REQ_USER=$2
 echo -n $"Starting $prog: "
 ulimit -S -c 0 >/dev/null 2>&1
 RETVAL=0
 for display in ${VNCSERVERS}
 do
 export USER="${display##*:}"
 if test -z "${REQ_USER}" -o "${REQ_USER}" == ${USER} ; then
 echo -n "${display} "
 unset BASH_ENV ENV
 DISP="${display%%:*}"
 export VNCUSERARGS="${VNCSERVERARGS[${DISP}]}"
 su ${USER} -c "cd ~${USER} && [ -f .vnc/passwd ] && vncserver :${DISP} ${VNCUSERARGS}"
 fi
 done
}
stop() {
 . /lib/lsb/init-functions
 REQ_USER=$2
 echo -n $"Shutting down VNCServer: "
 for display in ${VNCSERVERS}
 do
 export USER="${display##*:}"
 if test -z "${REQ_USER}" -o "${REQ_USER}" == ${USER} ; then
 echo -n "${display} "
 unset BASH_ENV ENV
 export USER="${display##*:}"
 su ${USER} -c "vncserver -kill :${display%%:*}" >/dev/null 2>&1
 fi
 done
 echo -e "\n"
 echo "VNCServer Stopped"
}
case "$1" in
start)
start $@
;;
stop)
stop $@
;;
restart|reload)
stop $@
sleep 3
start $@
;;
condrestart)
if [ -f /var/lock/subsys/vncserver ]; then
stop $@
sleep 3
start $@
fi
;;
status)
status Xvnc
;;
*)
echo $"Usage: $0 {start|stop|restart|condrestart|status}"
exit 1
esac

```  Then
  ```
sudo chmod +x /etc/init.d/vncserver
sudo mkdir -p /etc/vncserver
sudo nano /etc/vncserver/vncservers.conf

```  vncservers.conf
  ```
VNCSERVERS="1:vncuser"
VNCSERVERARGS[1]="-geometry 1024x768"

```  Bootup start entry:

  ```
sudo update-rc.d vncserver defaults 99

```  restart!
     

And now after connecting with the VNC I can see this:
[IMG]http://screenshu.com/static/uploads/temporary/g3/9t/6n/yt03zu.jpg[/IMG]

What should I do next to have the full Unity desktop?

---

