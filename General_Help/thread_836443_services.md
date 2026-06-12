---
title: "services"
date: 2008-06-21
forum: General Help
---

### Post by sulekha on 2008-06-21
Hi all,

i recently downloaded a command line utility named sysv-rc-conf for enabling/disabling services in different runlevels.This utility is showing
far more services than shown by system -> administration -> services GUI tool. now i am able to see many services such as brltty, loopback, rmnologin,dbus festival .....

now my question is as follows

what are the following services and what do they signify??

1)loopback
2)rmnologin
3)mtab
4)hotkey-se
5)module-in
6)mountvirt
7) urandom
8)brltty
9)festival

---

### Post by sdennie on 2008-06-21
I would imagine all these things have brief comments at the top of their respective init files.  Look in /etc/init.d/name_of_thing and check the top of the file.

---

### Post by ibuclaw on 2008-06-21
[LIST]
[*]**loopback** is to do with associating filesystems on your computer as files (ie: /dev/sda1), at least I think.
[*]**rmnologin** = Remote No Login (or remote login is disabled... I think).
[*]**mtab** is the daemon that holds the complete list of mounted filesystems on your PC (including virtual filesystems such as tmpfs and gvfs filesystems).
[*]not sure about **hotkey-se**... Although the word "HOTKEY" itself says alot about it.
[*]**module-in** I think is self explanitory ;) (Hint: /etc/modules)
[*]**mountvirt** handles your virtual filesystems (such as tmpfs and gvfs)
[*]**urandom** is the greatest tool in existance! (type in "echo $RANDOM" and you'll find out why) 
[*]**brltty** is a display driver.
[*]**festival** is the Linux version of "Microsoft Sam", is it not? (Probably the only one in the list that is worth turning off without thinking about the consequences).
[/LIST]
Regards
Iain

---

### Post by sulekha on 2008-06-22
> **vor said:**
> I would imagine all these things have brief comments at the top of their respective init files.  Look in /etc/init.d/name_of_thing and check the top of the file.

the following are the contents of my /etc/init.d/festival file


  #! /bin/sh
# /etc/init.d/festival
#
# Init script for starting Festival as a system-wide server process.
#
# Written by David Huggins-Daines <dhd@cepstral.com>

# Comment out the next line to start a Festival server at boot time.
exit 0
# NOTE: Not just anybody can connect to your server; the list of allowed
# hostnames is a regexp. Check /usr/share/festival/festival.scm for more
# helpful comments; add your settings to /etc/festival.scm.
#

set -e

DAEMON=/usr/bin/festival
REALPROC=/usr/bin/festival
NAME=festival

test -x $DAEMON || exit 0

case "$1" in
  start)
    echo -n "Starting Festival server: "
    start-stop-daemon --start --chuid nobody:audio --background \
		--exec $DAEMON -- --server
    echo "done."
    ;;
  stop)
    echo -n "Stopping Festival server: "
    start-stop-daemon --stop --oknodo --exec $REALPROC
    echo "done."
    ;;
  restart|reload|force-reload)
    echo "Restarting Festival server: "
    start-stop-daemon --stop --oknodo --exec $REALPROC
    start-stop-daemon --start --chuid nobody:audio --background \
		--exec $DAEMON -- --server
    echo "done."
    ;;
  *)
    echo "Usage: /etc/init.d/$NAME {start|stop|restart}"
    exit 1
    ;;
esac

exit 0


 but it doesn't say anything inn detail about what festival service does
 and what is it purpose in a manner understandable to a  lay user like me

---

### Post by p_quarles on 2008-06-22
Festival is a speech synthesizer. I've never seen it enabled by default, but if you have fiddled with the accessibility features it all, that could explain why it is there on startup.

It is not essential for system operation unless, I suppose, for a user with vision difficulties.

---

