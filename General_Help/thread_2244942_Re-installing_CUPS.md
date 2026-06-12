---
title: "Re-installing CUPS"
date: 2014-09-19
forum: General Help
---

### Post by cathect2 on 2014-09-19
Long story short, I've completely nuked my cups. I need to purge it and reinstall/reconfigure it. 

However, I've tried to purge and reinstall but when I try to start cups with ```
sudo /etc/init.d/cups restart
``` I get an error message:

```
cupsd: Child exited with status 1
```

Can someone help me?

---

### Post by dragonfly41 on 2014-09-19
Does your CUPS server work ... [http://localhost:631/](http://localhost:631/)

---

### Post by cathect2 on 2014-09-19
Nope. "Unable to Connect"

---

### Post by dragonfly41 on 2014-09-19
Some tips here in this old forum thread ...

[http://crunchbang.org/forums/viewtopic.php?id=53](http://crunchbang.org/forums/viewtopic.php?id=53)

---

### Post by cathect2 on 2014-09-19
I don't have cups in init.d. If I sudo etc/init.d/cups restart I get:

> command not found

---

### Post by tgalati4 on 2014-09-19
```
sudo service cups restart
```

Look in /var/log/cups for helpful messages.

Make sure that you have updated your packages and rebooted at least once.  CUPS is heavily dependent on the version of the kernel you are running.  If they get out of syncronization, you can have issues.

```
sudo apt-get update
sudo apt-get upgrade
sudo reboot
```

---

### Post by pqwoerituytrueiwoq on 2014-09-20
> **cathect2 said:**
> I don't have cups in init.d. If I sudo etc/init.d/cups restart I get:

you missed a slash before etc
[FONT=courier new]sudo /etc/init.d/cups restart [/FONT]
alternatively
[FONT=courier new]sudo service cups restart[/FONT]
or did you still want these commands
completely remove:
[FONT=courier new]sudo apt-get purge cups[/FONT]
install:
[FONT=courier new]sudo apt-get install cups[/FONT]
reconfigure
[FONT=courier new]sudo dpkg-reconfigure cups[/FONT]

---

### Post by cathect2 on 2014-09-20
PQW...

I just misstyped in my post. The command to restart cups went in correctly. I get "Command not Found." If I browse to /etc/init.d/ there is no cups there.

I just did the following:

1. I went through the (above) process of purging, reinstalling, and reconfiguring (which I had done twice before). 
2. I issued a cups restart I get: Command not found.
3. I restarted and initiated a cups restart. Same result: command not found. 

???

---

### Post by tgalati4 on 2014-09-20
What version of Ubuntu?  There is a bug (in 12.04 or 12.10) where CUPS will fail to start if *avahi-daemon* is not running.  Avahi is the Bonjour-like service discovery daemon that advertises printers and other services.  The fix is to make sure avahi is running:

tgalati4@Mint14-Extensa ~ $ ps aux | grep avahi
avahi      580  0.0  0.0  32304  1752 ?        S    Sep18   0:00** avahi-daemon: running** [Mint14-Extensa.local]
avahi      581  0.0  0.0  32180   476 ?        S    Sep18   0:00 avahi-daemon: chroot helper
tgalati4  6292  0.0  0.0  13588   932 pts/0    S+   07:46   0:00 grep --colour=auto avahi

The *cups* script points to upstart.  So if upstart is broken, then cups won't start correctly:

lrwxrwxrwx   1 root root    21 Apr 18 09:52 **cups -> /lib/init/upstart-job**

---

### Post by cathect2 on 2014-09-20
Howdy, tgalati. 

I'm using [B]14.04.

[/B]One thing I notice: if I browse to /etc/init.d/ there is no executable named "cups" even after the purge and reinstall. Why is that? I only have "cups-browsed."

I can confirm that avahi is running...

---

### Post by sandyd on 2014-09-20
Try to reinstall cups-daemon (which contains /etc/init.d/cups)

---

### Post by cathect2 on 2014-09-20
I used synaptic to reinstall cups-daemon. However, cups does not appear in /etc/init.d/

---

### Post by dragonfly41 on 2014-09-20
Although you have wriiten (post #8) that you have purged and reinstalled ..

According to advice in this thread ...

[https://lists.debian.org/debian-user/2012/03/msg00952.html](https://lists.debian.org/debian-user/2012/03/msg00952.html)

Try 'apt-get remove cups' followed by a reinstall.

---

### Post by pqwoerituytrueiwoq on 2014-09-20
make sure cups-daemon is installed, it is a dependency of cups so it should be, it is the one that contains /etc/init.d/cups
```
apt-cache policy cups-daemon cups
cups-daemon:
  Installed: 1.7.2-0ubuntu1.2
  Candidate: 1.7.2-0ubuntu1.2
  Version table:
 *** 1.7.2-0ubuntu1.2 0
        500 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main amd64 Packages
        500 http://security.ubuntu.com/ubuntu/ trusty-security/main amd64 Packages
        100 /var/lib/dpkg/status
     1.7.2-0ubuntu1 0
        500 http://us.archive.ubuntu.com/ubuntu/ trusty/main amd64 Packages
cups:
  Installed: 1.7.2-0ubuntu1.2
  Candidate: 1.7.2-0ubuntu1.2
  Version table:
 *** 1.7.2-0ubuntu1.2 0
        500 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main amd64 Packages
        500 http://security.ubuntu.com/ubuntu/ trusty-security/main amd64 Packages
        100 /var/lib/dpkg/status
     1.7.2-0ubuntu1 0
        500 http://us.archive.ubuntu.com/ubuntu/ trusty/main amd64 Packages
```

---

### Post by cathect2 on 2014-09-20
Completely bizarre. So I can confirm that the daemon is installed using your method PQW. However, if I browse there it doesn't seem to exist. No cups in init.d. Weird.

---

### Post by pqwoerituytrueiwoq on 2014-09-20
maybe this will fix it
all at once:
```
sudo apt-get purge -y cups cups-daemon && sudp apt-get --purge -y autoremove && sudo apt-get update && sudo apt-get clean && sudo apt-get install -y cups
```
one my one the manual way:
```
sudo apt-get purge cups cups-daemon
sudp apt-get --purge autoremove
sudo apt-get update
sudo apt-get clean
sudo apt-get install cups
```

---

### Post by tgalati4 on 2014-09-20
In 12.10 cups points to an upstart (services) script.  In 14.04 it goes back to a real control script:

> gates@GNAS /etc/init.d $ cat cups
#! /bin/sh
### BEGIN INIT INFO
# Provides:          cups
# Required-Start:    $syslog $remote_fs
# Required-Stop:     $syslog $remote_fs
# Should-Start:      $network avahi-daemon slapd nslcd
# Should-Stop:       $network
# X-Start-Before:    samba
# X-Stop-After:      samba
# Default-Start:     2 3 4 5
# Default-Stop:      1
# Short-Description: CUPS Printing spooler and server
# Description:       Manage the CUPS Printing spooler and server;
#                    make it's web interface accessible on [http://localhost:631/](http://localhost:631/)
### END INIT INFO

# Author: Debian Printing Team <debian-printing@lists.debian.org>

PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin
DAEMON=/usr/sbin/cupsd
NAME=cupsd
PIDFILE=/var/run/cups/$NAME.pid
DESC="Common Unix Printing System"
SCRIPTNAME=/etc/init.d/cups

unset TMPDIR

# Exit if the package is not installed
test -x $DAEMON || exit 0

mkdir -p /var/run/cups/certs
[ -x /sbin/restorecon ] && /sbin/restorecon -R /var/run/cups

# Read configuration variable file if it is present
if [ -r /etc/default/cups ]; then
  . /etc/default/cups
fi

# Define LSB log_* functions.
# Depend on lsb-base (>= 3.2-14) to ensure that this file is present
# and status_of_proc is working.
. /lib/lsb/init-functions

# Get the timezone set.
if [ -z "$TZ" -a -e /etc/timezone ]; then
    TZ=`cat /etc/timezone`
    export TZ
fi

coldplug_usb_printers() {
    if type udevadm > /dev/null 2>&1 && [ -x /lib/udev/udev-configure-printer ]; then
	for printer in `udevadm trigger --verbose --dry-run --subsystem-match=usb \
		--attr-match=bInterfaceClass=07 --attr-match=bInterfaceSubClass=01 2>/dev/null || true; \
	                udevadm trigger --verbose --dry-run --subsystem-match=usb \
		--sysname-match='lp[0-9]*' 2>/dev/null || true`; do
	    /lib/udev/udev-configure-printer add "${printer#/sys}"
	done
    fi
}

case "$1" in
  start)
	log_daemon_msg "Starting $DESC" "$NAME"

	mkdir -p `dirname "$PIDFILE"`
	if [ "$LOAD_LP_MODULE" = "yes" -a -f /usr/lib/cups/backend/parallel \
             -a -f /proc/devices -a -f /proc/modules -a -x /sbin/modprobe ]; then
	  modprobe -q -b lp || true
	  modprobe -q -b ppdev || true
	  modprobe -q -b parport_pc || true
	fi

	start-stop-daemon --start --quiet --oknodo --pidfile "$PIDFILE" --exec $DAEMON
	status=$?
	[ $status = 0 ] && coldplug_usb_printers
	log_end_msg $status
	;;
  stop)
	log_daemon_msg "Stopping $DESC" "$NAME"
	start-stop-daemon --stop --quiet --retry 5 --oknodo --pidfile $PIDFILE --name $NAME
	status=$?
	log_end_msg $status
	;;
  reload|force-reload)
       log_daemon_msg "Reloading $DESC" "$NAME"
       start-stop-daemon --stop --quiet --pidfile $PIDFILE --name $NAME --signal 1
       status=$?
       log_end_msg $status
       ;;
  restart)
	log_daemon_msg "Restarting $DESC" "$NAME"
	if start-stop-daemon --stop --quiet --retry 5 --oknodo --pidfile $PIDFILE --name $NAME; then
		start-stop-daemon --start --quiet --pidfile "$PIDFILE" --exec $DAEMON
	fi
	status=$?
	log_end_msg $status
	;;
  status)
	status_of_proc -p "$PIDFILE" "$DAEMON" "$NAME" && exit 0 || exit $?
	;;
  *)
	echo "Usage: $SCRIPTNAME {start|stop|restart|force-reload|status}" >&2
	exit 3
	;;
esac

exit 0


---

