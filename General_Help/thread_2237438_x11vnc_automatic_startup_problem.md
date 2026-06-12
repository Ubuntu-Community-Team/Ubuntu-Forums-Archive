---
title: "x11vnc automatic startup problem"
date: 2014-08-01
forum: General Help
---

### Post by cjsmall on 2014-08-01
I have read many of the vnc threads on this and other forums and spent a couple of days tweaking the startup script, but cannot get x11vnc to automatically start in a state that will accept remote connections.

On an Xubuntu 14.04 system, I have installed x11vnc.  When I manually start it using:

    x11vnc -shared -forever -loop -usepw -geometry  1550x871 &

I can connect to the server from my remote Solaris system.  Great.  So I want this to start automatically, and create the file /etc/init.d/vnc_server with the following content:


#!/bin/sh -e
### BEGIN INIT INFO
##############################################################################
# Provides:          vncserver
# Required-Start:    networking
# Required-Stop:     networking
# Default-Start:     2 3 4 5
# Default-Stop:      0 1 6
##############################################################################
### END INIT INFO

##############################################################################
# Configuration
##############################################################################

PATH="/bin:/usr/bin:/sbin:/usr/sbin"

PROG="/etc/init.d/vnc_server"

. /lib/lsb/init-functions           # Load support functions

GEOMETRY="1550x871"             # Desktop geometry: "WxH"

VNC_PATH="/usr/bin"             # Location of VNC server
VNC_SERVER="x11vnc"             # VNC server name

VNC_OPTS="-shared -forever -loop -usepw -geometry ${GEOMETRY} \
      -auth /var/run/lightdm/root/:0 -users +jeff"

if [ ! -x ${VNC_PATH}/${VNC_SERVER} ] ; then
    log_failure_msg "${VNC_PATH}/${VNC_SERVER} missing or not executable."
    exit 1
fi

case "$1" in
start)
    log_action_begin_msg \
        "Starting vncserver on localhost${DISPLAY}"
    ${VNC_PATH}/${VNC_SERVER} ${VNC_OPTS} >/dev/null 2>&1 &
    ;;
stop)
    log_action_begin_msg \
        "Stoping vncserver on localhost${DISPLAY}"
    pkill ${VNC_SERVER}
    ;;
restart)
    ${PROG} stop
    ${PROG} start
    ;;
esac

exit

When I reboot, x11vnc is running as a process owned by root:

    # ps -ef | grep x11vnc
    root       3586  1891  0 14:15 pts/9    00:00:00 /usr/bin/x11vnc -shared -forever 
    -loop -usepw -geometry 1550x871 -auth /var/run/lightdm/root/:0 -users +jeff

However, attempts to connect are refused:

    vncviewer: ConnectToTcpAddr: connect: Connection refused
    Unable to connect to VNC server

If I issue a restart:

    sudo /etc/init/vnc_server restart

then I get two new x11vnc process running, one owned by root and the other by me:

    # ps -ef | grep x11vnc
    root      3893  1891  0 14:15 pts/9    00:00:00 /usr/bin/x11vnc -shared -forever \
    -loop -usepw -geometry 1550x871 -auth /var/run/lightdm/root/:0 -users +jeff

    jeff      3894  3893  1 14:15 pts/9    00:00:00 /usr/bin/x11vnc -shared -forever \
    -loop -usepw -geometry 1550x871 -auth /var/run/lightdm/root/:0 -users +jeff

Now I can access the vnc server.

Note that I have tried the -users option with a variety of user names, but the original process is never handed off.  I also added the -auth option, but that made no difference.  I don't know wht thisa would matter, but my user (jeff) is automatically logged in upon boot.

1: Why does the original process not get handed off to the user specified by -users as the manual states?

2: Why can't I connect to the original process owned by root?

3: Why are two processes spawned upon a restart?

---

### Post by steeldriver on 2014-08-01
You seem to be assuming that you can start an x11vnc server in the same way as a standalone VNC server like vnc4server / tightvncserver - I'm not sure that's the case (or, at least, it's not the usual way to do it).

What I mean is x11vnc (like the gnome default vino-server) is a *desktop sharing* server, that expects to be run from a user-session and to connect to the real X server for that session. When you start it as a service, the user-session (and possibly the X server) is not running. In contrast, things like vnc4server / tightvncserver start self-contained headless X servers and relay *those* over VNC and don't care what  real X server / sessions are running on the host.

If you don't want to start x11vnc from a local desktop session, then there's a way to allow remote *login* via x11vnc using lightdm/upstart --> [Remote VNC login to Ubuntu 11.10]("http://mlepicki.com/2011/10/remote-vnc-login-to-ubuntu-11-10/") (NOTE: it's described for 11.10, but I've used it on 12.04 and I think it *should* work on 14.04)

Hope this helps

---

### Post by cjsmall on 2014-08-01
Steeldriver:  Thanks for the explanation.  That makes sense.  I think I got derailed because of there being so many other discussions that seem to describe this very thing that I was trying to do, yet following the instructions never worked.  I'll look at the document you reference above.  Regards.

---

