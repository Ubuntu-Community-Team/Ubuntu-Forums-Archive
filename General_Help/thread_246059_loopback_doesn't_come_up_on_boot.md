---
title: "loopback doesn't come up on boot"
date: 2006-08-28
forum: General Help
---

### Post by ultralame on 2006-08-28
When I boot/reboot, my dapper installation comes up to the GUI.  However, the network is not started.

HEre's what I have to do:
[LIST]
[*]From the GUI, bring up the Networking panel and activate eth0.
[*]Run a script that creates the loopback interface
[*]init 3
[*]init 2
[*] (those last parts restart all my services/daemons with the network up)- is there a better way to do that?
[/LIST]

Any ideas?  I am not sure what to post here.  The scripts in rcS.d and rc2.d appear to be correct (the loopback is created and then eth0 is started).

I can't seem to find anything in /var/log/syslog, /var/log/messages or dmesg that indicates a problem.

Any ideas?  How can I debug this?  Is there a way to boot slowly, toggle startup scripts as I go, and then read the output of each one?

Thanks!

---

### Post by Jaime E. Villate on 2006-10-06
I had the same problem. I could get the loopback interface back with
```
sudo ifconfig lo up
```
but the problems continued because "lo" was not being brought up automatically at bootime. I finally found the cause of the problem by following the advice of varunus in thread 48557: run
```
sudo /etc/init.d/networking restart
```
manually to detect the problem: it pinpointed a simple syntax error in /etc/network/interfaces which was causing the problem.

---

### Post by ultralame on 2006-10-06
OK- that's interesting.  But what was the Syntax Error you found?  I have two scripts:
  /etc/init.d/networking
  /etc/init.d/loopback

In rcS.d, the loopback is run first, then the networking.

Notice in the networking script, the START command runs
[INDENT]ifup -a[/INDENT]
while the RESTART command runs
[INDENT]ifdown -a --exclude=lo
ifup -a --exclude=lo[/INDENT]

Is this the problem?  That when the machine starts, it screws up the lo interface, but not when you use STOP or RESTART?

/etc/init.d/networking:
```
#!/bin/sh -e
### BEGIN INIT INFO
# Provides:          networking
# Required-Start:    mountvirtfs ifupdown $local_fs
# Default-Start:     S
# Default-Stop:      0 6
### END INIT INFO

PATH="/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin"

[ -x /sbin/ifup ] || exit 0

. /lib/lsb/init-functions


case "$1" in
start)
        log_action_begin_msg "Configuring network interfaces"
        type usplash_write >/dev/null 2>/dev/null && usplash_write "TIMEOUT 120" || true
        if [ "$VERBOSE" != no ]; then
            if ifup -a; then
                log_action_end_msg $?
            else
                log_action_end_msg $?
            fi
        else
            if ifup -a >/dev/null 2>&1; then
                log_action_end_msg $?
            else
                log_action_end_msg $?
            fi
        fi
        type usplash_write >/dev/null 2>/dev/null && usplash_write "TIMEOUT 15" || true
        ;;

stop)
        if sed -n 's/^[^ ]* \([^ ]*\) \([^ ]*\) .*$/\2/p' /proc/mounts |
                grep -qE '^(nfs[1234]?|smbfs|ncp|ncpfs|coda|cifs)$'; then
            log_warning_msg "not deconfiguring network interfaces: network shares still mounted."
            exit 0
        fi

        log_action_begin_msg "Deconfiguring network interfaces"
        if [ "$VERBOSE" != no ]; then
            if ifdown -a --exclude=lo; then
                log_action_end_msg $?
            else
                log_action_end_msg $?
            fi
        else
            if ifdown -a --exclude=lo >/dev/null 2>/dev/null; then
                log_action_end_msg $?
            else
                log_action_end_msg $?
            fi
        fi
        ;;

force-reload|restart)
        log_action_begin_msg "Reconfiguring network interfaces"
        ifdown -a --exclude=lo || true
        if ifup -a --exclude=lo; then
            log_action_end_msg $?
        else
            log_action_end_msg $?
        fi
        ;;

*)
        echo "Usage: /etc/init.d/networking {start|stop|restart|force-reload}"
        exit 1
        ;;
esac

exit 0
```

/etc/init.d/loopback:
```
#!/bin/sh -e
#
# loopback - brings up the loopback (127.0.0.1) network device so that
#            DHCP and other such things will work
#

# Check the package is still installed
[ -x /sbin/ifup ] || exit 0

# Get LSB functions
. /lib/lsb/init-functions
. /etc/default/rcS

case "$1" in
    start)
        [ -d /var/run/network ] || mkdir /var/run/network

        log_begin_msg "Starting basic networking..."
#       if ifup -v --allow auto lo; then
        if ifup -v auto lo; then
            log_end_msg 0
        else
            log_end_msg $?
        fi
        ;;
    stop)
        log_begin_msg "Stopping basic networking..."
        if ifdown lo; then
            log_end_msg 0
        else
            log_end_msg $?
        fi
        ;;
    restart|force-reload)
        exit 0
        ;;
    *)
        echo "Usage: /etc/init.d/loopback {start|stop|restart|force-reload}"
        exit 1
        ;;
esac

exit 0
```

---

### Post by NigO on 2008-02-01
I'm having a similar problem with one machine.
/etc/network/interfaces contains  (XX's replace valid internal addresses)
```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 10.XX.XX.XX
netmask 255.255.255.0
gateway 10.XX.XX.XX


#iface eth1 inet dhcp

#auto eth2
#iface eth2 inet dhcp

#auto ath0
#iface ath0 inet dhcp

#auto wlan0
#iface wlan0 inet dhcp


```

On boot loopback doesn't come up.  I need to use 
```
sudo ifconfig lo up 
```

If I do 
```
sudo ifup --verbose lo 
``` 
before bringing the interface up instead, I get 
```
ifup: interface lo already configured

```

and ```
 ifup -a
```
doesn't bring it up either.
```
ifconfig -a
``` shows that it is configured, but not up.

If I edit the standard /etc/init.d/networking script so that restart doesn't exclude lo (see previous messages above), then /etc/init.d/networking restart does fix the problem.

Any clues where to go next?

---

