---
title: "Help on init.d script for rtorrent through Screen"
date: 2007-10-24
forum: General Help
---

### Post by Jungleboss on 2007-10-24
Rtorrent won't start. No screen session for it exist after boot or after running ```
sudo /etc/init.d/rtorrent start
 * Starting Torrent Client:
 *    Starting rtorrent..                                                [ OK ] 

```
This is my script concerning the startup. This syntax works well for starting up hellanzb but apparently not for rtorrent.

```
#! /bin/bash
NAME=rtorrent
USERNAME=xxxx
RTORRENT_PIDFILE=/var/run/rtorrent.pid
RTORRENT_BIN=/usr/local/bin/rtorrent
DESC="Torrent Client:"

trap "" 1
export LANG=C

. /lib/lsb/init-functions

case "$1" in
  start)
    log_action_msg "Starting $DESC"

    log_daemon_msg "   Starting $NAME.."
    if start-stop-daemon -S -c $USERNAME -m -b --pidfile $RTORRENT_PIDFILE --exec /usr/bin/screen -- -S $NAME -D -m $RTORRENT_BIN; then
	    log_end_msg 0
	else
	    log_end_msg 1
	fi
    ;;
```

if I manually run, with the same user the scripts uses:
```
/usr/bin/screen -S rtorrent -D -m /usr/local/bin/rtorrent
```

.. it works.

---

### Post by Jungleboss on 2007-10-25
Does someone have any ideas, please?

---

### Post by digitalbenji on 2007-10-25
What runlevel is that happening in?  I imagine that a screen in a runlevel 3 environment is not going to last when the system punches into runlevel 5.  I could be wrong though.

---

### Post by Jungleboss on 2007-10-25
I thought Ubuntu only used runlevel  2 (like Debian).

Also I run other init.d scripts with the same syntax for other text based applications that work.

It seems there's something with start-stop-daemon and rtorrent that doesn't work well together. At least with the parameters I'm using.

---

### Post by airtonix on 2007-11-09
is this for automatically starting rtorrent on system bootup?

so that you can still access a system remotely if it had auto startup after failaure?

---

### Post by OptikKnight on 2008-04-13
Greetings,

Has this question been resolved? I developed a similar solution for Gentoo, and it might be usable on Ubuntu. I'd be interested to see what other people have come up with...

Regards,

S

---

