---
title: "LXDE and VNC - can't start the service."
date: 2013-12-29
forum: General Help
---

### Post by prayner.basil on 2013-12-29
Hi

I'm trying to setup a VNC service to access a graphical desktop (cos I'm a Linux noob, and I'm much more comfortable with a GUI than a CLI).

My server is [COLOR=#000000][FONT=Arial]XenServer6.2, and I'm using the client from a Windows box on my home network. Both server and client are on my home network. I have a static IP, and eventually I'd like to make the Ubuntu 12.04 OS available to others across the web for MUD/MOO servers and also web server.
[/FONT][/COLOR]
This is a fresh installation to essentially learn more about virtualization. Prior to this I just had Ubuntu installed directly and ran these services.

To administer the Ubuntu server using the XenCentre client, I really want to have a GUI.

I followed this tutorial to install LXDE and VNC - [http://myhosting.com/wiki/index.php?/article/AA-04694/0/Ubuntu-VPS-Desktop-LXDE-Installation-and-VNC.html](http://myhosting.com/wiki/index.php?/article/AA-04694/0/Ubuntu-VPS-Desktop-LXDE-Installation-and-VNC.html)

When I try to start the VNC service with **service vncserver start, **it gives the following error.


/etc/init.d/vncserver: line 8: unset: `VNCSERVERS=': not a valid identifier
/etc/init.d/vncserver: line 8: unset: `[': not a valid identifier
/etc/init.d/vncserver: line 8: unset: `-f': not a valid identifier
/etc/init.d/vncserver: line 8: unset: `/etc/vncserver/vncservers.conf': not a valid identifier
/etc/init.d/vncserver: line 8: unset: `]': not a valid identifier
/etc/init.d/vncserver: line 9: syntax error near unexpected token `&&'
/etc/init.d/vncserver: line 9: `&& . /etc/vncserver/vncservers.conf prog=$"VNC server" start() {'
root@ubuntu:~# 

I've Googled solutions - obviously where UI found the tutorial. But I haven't been able to solve the problems I currently have.
I'd appreciate any advice you may be able to give.

---

### Post by steeldriver on 2013-12-29
Did you copy/paste the /etc/init.d/vncserver file from the webpage you linked? if so I'd suspect it got corrupted (some non-printing characters, line wrapping, or Windows line terminations crept in maybe?) - try looking at it with cat -net

```
cat -net /etc/init.d/vncserver
```

---

### Post by prayner.basil on 2013-12-30
Thanks steeldriver. Followed your advice (To the best of my ability anyway).  Copied the code from the web, dumped it into an ascii editor (programmers notepad), and then pasted it into [COLOR=#000000][FONT=Arial]/etc/init.d/vncserver
[/FONT][/COLOR] 
The error is unchanged I think \:

root@ubuntu:~# service vncserver start
/etc/init.d/vncserver: line 8: unset: `VNCSERVERS=': not a valid identifier
/etc/init.d/vncserver: line 8: unset: `[': not a valid identifier
/etc/init.d/vncserver: line 8: unset: `-f': not a valid identifier
/etc/init.d/vncserver: line 8: unset: `/etc/vncserver/vncservers.conf': not a valid identifier
/etc/init.d/vncserver: line 8: unset: `]': not a valid identifier
/etc/init.d/vncserver: line 9: syntax error near unexpected token `&&'
/etc/init.d/vncserver: line 9: `&& . /etc/vncserver/vncservers.conf prog=$"VNC server" start() {'

I'd still like advice if anyone has ideas.

---

### Post by steeldriver on 2013-12-30
well clearly all those things should not be on line 8 - here's what I get 

```

$ cat -net vncserver | head -20
     1    #!/bin/bash$
     2    ### BEGIN INIT INFO$
     3    # Provides:          vncserver$
     4    # Required-Start:    $syslog$
     5    # Required-Stop:     $syslog$
     6    # Default-Start:     2 3 4 5$
     7    # Default-Stop:      0 1 6$
     8    # Short-Description: vnc server$
     9    # Description:$
    10    #$
    11    ### END INIT INFO$
    12    $
    13    unset VNCSERVERARGS$
[COLOR=#0000ff][B]    14    VNCSERVERS=""$
    15    [ -f /etc/vncserver/vncservers.conf ] && . /etc/vncserver/vncservers.conf$
    16    prog=$"VNC server"$
[/B] [/COLOR]   17    $
    18    start() {$
    19     . /lib/lsb/init-functions$
    20     REQ_USER=$2$

```

What does yours look like?

---

### Post by prayner.basil on 2013-12-30
Thanks Steeldriver. This is a copy and paste from the Xenserver console.

1#!/bin/bash$
     2### BEGIN INIT INFO$
     3# Provides: vncserver Required-Start: $syslog Required-Stop: $syslog $
     4# Default-Start: 2 3 4 5 Default-Stop: 0 1 6 Short-Description: vnc $
     5# server Description:$
     6#$
     7### END INIT INFO$
     8unset VNCSERVERARGS VNCSERVERS="" [ -f /etc/vncserver/vncservers.conf ] $
     9&& . /etc/vncserver/vncservers.conf prog=$"VNC server" start() {$
    10 . /lib/lsb/init-functions$
    11 REQ_USER=$2$
    12 echo -n $"Starting $prog: "$
    13 ulimit -S -c 0 >/dev/null 2>&1$
    14 RETVAL=0$
    15 for display in ${VNCSERVERS}$
    16 do$
    17 export USER="${display##*:}"$
    18 if test -z "${REQ_USER}" -o "${REQ_USER}" == ${USER} ; then$
    19 echo -n "${display} "$
    20 unset BASH_ENV ENV$
	21 DISP="${display%%:*}"$
    22 export VNCUSERARGS="${VNCSERVERARGS[${DISP}]}"$
    23 su ${USER} -c "cd ~${USER} && [ -f .vnc/passwd ] && vncserver :${DISP} $
    24${VNCUSERARGS}"$
    25 fi$
    26 done$
    27}$
    28stop() {$
    29 . /lib/lsb/init-functions$
    30 REQ_USER=$2$
    31 echo -n $"Shutting down VNCServer: "$
    32 for display in ${VNCSERVERS}$
    33 do$
    34 export USER="${display##*:}"$
    35 if test -z "${REQ_USER}" -o "${REQ_USER}" == ${USER} ; then$
    36 echo -n "${display} "$
    37 unset BASH_ENV ENV$
    38 export USER="${display##*:}"$
    39 su ${USER} -c "vncserver -kill :${display%%:*}" >/dev/null 2>&1$
    40 fi$
	41 done$
    42 echo -e "\n"$
    43 echo "VNCServer Stopped"$
    44}$
    45case "$1" in start) start $@ ;; stop) stop $@ ;; restart|reload) stop $@ $
    46sleep 3 start $@ ;; condrestart) if [ -f /var/lock/subsys/vncserver ]; $
    47then stop $@ sleep 3 start $@ fi ;; status) status Xvnc ;; *) echo $
    48$"Usage: $0 {start|stop|restart|condrestart|status}" exit 1$
    49esac$

---

### Post by steeldriver on 2013-12-30
so... as suspected... all the comment lines and everything at least down to the start() call (your line 9 - but should be line 18) is messed up

I suggest you copy the whole thing again, maybe use a different editor?

---

### Post by prayner.basil on 2013-12-30
Thanks for the advice. I switched to Vim, and the VNC service started without error.

Opened port 59xx, and all appears good.

Thanks so much for your patience and persistence.

If I want to allow users outside my network to access the Ubuntu server via VNC, can I do that, or is SSH access preferred?

---

### Post by steeldriver on 2013-12-30
no problem - glad you got it working

fwiw if your server is exposed to the public internet then I STRONGLY recommend tunnelling the VNC connection over SSH and closing / firewalling the actual VNC port

---

