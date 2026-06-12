---
title: "Trying to connect using vnc from iPad"
date: 2014-10-06
forum: General Help
---

### Post by kkmo on 2014-10-06
Hello, I have 14.04 and am trying to use vnc (using Jump) from an iPad.  If there is a better way than what I am trying, great.  I just want to be able to connect securely from an iPad.
I have installed vnc4server, and Jump, on the iPad is configured to use port 5900 and ssh on port 22.
From the iPad it asks for my ssh password, accepts it, but then closes. 
 
I looked at /var/log/auth.log and it shows:
sshd[3779]: Set /proc/self/oom_score_adj to 0
sshd[3779]: Connection from [iPad] port 65529 on [Ubuntu server] port 22
sshd[3779]: Accepted password for MyAccount from [iPad] port 65529 ssh2
sshd[3779]: User child is on pid 3781
sshd[3782]: Set /proc/self/oom_score_adj to 0
sshd[3782]: Connection from [Ubuntu server] port 50802 on [Ubuntu server] port 5900
sshd[3781]: Connection closed by [iPad]
sshd[3781]: Transferred: sent 2688, received 1192 bytes
sshd[3781]: Closing connection to [iPad] port 65529
sshd[3782]: Did not receive identification string from [Ubuntu server]
 
 
my vncservers.conf is:
VNCSERVERS="1:MyAccount"
VNCSERVERARGS[1]="-geometry 1024x768 -depth 24"
 
And my /etc/init.d/vncserver is:
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
                            su ${USER}|> -c "cd ~${USER} && [ -f .vnc/passwd ] && vnc4server :${DISP} ${VNCUSERARGS}"
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
                            su ${USER} -c "vnc4server -kill :${display%%:*}" >/dev/null 2>&1
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
 
Any ideas?  Thanks

---

