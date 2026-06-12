---
title: "SSHD on startup?"
date: 2007-03-01
forum: General Help
---

### Post by WetWired on 2007-03-01
Hey all, I've installed ubuntu server and I'd like to be able to access the machine exclusively through ssh. I was needing to know what I need to do in order to run an ssh server on the machine, and make it load on startup. Even so I can login to the box via ssh.

---

### Post by scxtt on 2007-03-01
the only way i can think of involves a GUI, which i'm pretty sure it just generates /etc/init.d/ssh or copies it from /etc/rc*.d ...

what does **sudo find /etc -name ssh -exec ls -l {} \;** return?

---

### Post by WetWired on 2007-03-01
total 140
-rw-r--r-- 1 root root 132839 2006-05-17 19:43 moduli
-rw-r--r-- 1 root root 1361 2006-05-17 19:43 ssh_config

---

### Post by scxtt on 2007-03-01
try creating /etc/init.d/ssh w/ the following contents {assuming you have openssh-server installed}:
```
[font=courier]#! /bin/sh
set -e

# /etc/init.d/ssh: start and stop the OpenBSD "secure shell(tm)" daemon

test -x /usr/sbin/sshd || exit 0
( /usr/sbin/sshd -\? 2>&1 | grep -q OpenSSH ) 2>/dev/null || exit 0

if test -f /etc/default/ssh; then
    . /etc/default/ssh
fi

. /lib/lsb/init-functions

check_for_no_start() {
    # forget it if we're trying to start, and /etc/ssh/sshd_not_to_be_run exists
    if [ -e /etc/ssh/sshd_not_to_be_run ]; then
        log_end_msg 0
        log_warning_msg "OpenBSD Secure Shell server not in use (/etc/ssh/sshd_not_to_be_run)"
        exit 0
    fi
}

check_privsep_dir() {
    # Create the PrivSep empty dir if necessary
    if [ ! -d /var/run/sshd ]; then
        mkdir /var/run/sshd
        chmod 0755 /var/run/sshd
    fi
}

check_config() {
    if [ ! -e /etc/ssh/sshd_not_to_be_run ]; then
        /usr/sbin/sshd -t || exit 1
    fi
}

export PATH="${PATH:+$PATH:}/usr/sbin:/sbin"

case "$1" in
  start)
        log_begin_msg "Starting OpenBSD Secure Shell server..."
        check_for_no_start
        check_privsep_dir
        start-stop-daemon --start --quiet --pidfile /var/run/sshd.pid --exec /usr/sbin/sshd -- $SSHD_OPTS || log_end_msg 1
        log_end_msg 0
        ;;
  stop)
        log_begin_msg "Stopping OpenBSD Secure Shell server..."
        start-stop-daemon --stop --quiet --oknodo --pidfile /var/run/sshd.pid || log_end_msg 1
        log_end_msg 0
        ;;

  reload|force-reload)
        log_begin_msg "Reloading OpenBSD Secure Shell server's configuration"
        check_for_no_start
        check_config
        start-stop-daemon --stop --signal 1 --quiet --oknodo --pidfile /var/run/sshd.pid --exec /usr/sbin/sshd || log_end_msg 1
        log_end_msg 0
        ;;

  restart)
        log_begin_msg "Restarting OpenBSD Secure Shell server..."
        check_privsep_dir
        check_config
        start-stop-daemon --stop --quiet --oknodo --retry 30 --pidfile /var/run/sshd.pid
        check_for_no_start
        start-stop-daemon --start --quiet --pidfile /var/run/sshd.pid --exec /usr/sbin/sshd -- $SSHD_OPTS || log_end_msg 1
        log_end_msg 0
        ;;

  *)
        log_success_msg "Usage: /etc/init.d/ssh {start|stop|reload|force-reload|restart}"
        exit 1
esac

exit 0[/font]
```

---

### Post by WW on 2007-03-01
I'm pretty sure that if you install the package **openssh-server**, it will automatically be configured to start up when you boot.  See if it "just works", before you start messing around with the configuration files.

---

### Post by scxtt on 2007-03-01
> **WW said:**
> I'm pretty sure that if you install the openssh-server, it will automatically be configured to start up when you boot.  See if it "just works", before you start messing around with the configuration files.what i suggested doesn't mess w/ a config file, just adds a script to /etc/init.d/ to start SSH on boot ... basically it's the result of me selecting "Open SSH Server" via a KDE GUI interface ... not sure what it was like upon install since i always install SSH and enable that anytime i load the OS from scratch ...

---

### Post by Mr. C. on 2007-03-01
You can't run the server with just an init script - that will only attempt to start the ssh daemon.  But it doesn't yet exist on the OPs system, so the OP needs to install the sshd server package as suggested.  And no GUI is required for SSH logins.

---

### Post by WetWired on 2007-03-01
> **WW said:**
> I'm pretty sure that if you install the package **openssh-server**, it will automatically be configured to start up when you boot.  See if it "just works", before you start messing around with the configuration files.

You are correct, sir. It did.

Thank you all for your assistance.

---

### Post by scxtt on 2007-03-02
> **Mr. C. said:**
> You can't run the server with just an init script - that will only attempt to start the ssh daemon.  But it doesn't yet exist on the OPs system, so the OP needs to install the sshd server package as suggested.  And no GUI is required for SSH logins.silly me, i assumed he already had "openssh-server" installed but it WASN'T autostarting on boot ...

:tongue:

[sarcasm]
and yes, i'm very aware of what you said above - it's almost insulting you said it ;)
[/sarcasm]

---

### Post by Mr. C. on 2007-03-02
Its just for the record and searches; nothing personal.

---

