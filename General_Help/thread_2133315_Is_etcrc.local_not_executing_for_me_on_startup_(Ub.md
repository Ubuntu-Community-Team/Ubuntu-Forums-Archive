---
title: "Is /etc/rc.local not executing for me on startup (Ubuntu 12.10)?"
date: 2013-04-07
forum: General Help
---

### Post by VanderveckenSmith on 2013-04-07
I recently had an external enclosure go down.  I was on Ubuntu 12.04 and I had "sudo zfs mount $poolname" in /etc/rc.local, which automounted the pool at startup.
As part of attempts to troubleshoot, I upgraded to 12.10.  Now, with a working enclosure. I no longer get automounting on startup.  If I open a terminal after startup and copy-paste from rc.local, the zfs pool mounts just fine, but somewhere during startup this command must be failing.  How can I find out what's going on?

---

### Post by SeijiSensei on 2013-04-07
There should be a symlink to /etc/init.d/rc.local in /etc/rc2.d called S99rc.local.  Is it there? /etc/init.d/rc.local invokes /etc/rc.local like this:
```

# more /etc/init.d/rc.local
#! /bin/sh
### BEGIN INIT INFO
# Provides:          rc.local
# Required-Start:    $remote_fs $syslog $all
# Required-Stop:
# Default-Start:     2 3 4 5
# Default-Stop:
# Short-Description: Run /etc/rc.local if it exist
### END INIT INFO


PATH=/sbin:/usr/sbin:/bin:/usr/bin

. /lib/init/vars.sh
. /lib/lsb/init-functions

do_start() {
        if [ -x /etc/rc.local ]; then
                [ "$VERBOSE" != no ] && log_begin_msg "Running local boot script
s (/etc/rc.local)"
                /etc/rc.local
                ES=$?
                [ "$VERBOSE" != no ] && log_end_msg $ES
                return $ES
        fi
}

case "$1" in
    start)
        do_start
        ;;
    restart|reload|force-reload)
        echo "Error: argument '$1' not supported" >&2
        exit 3
        ;;
    stop)
        ;;
    *)
        echo "Usage: $0 start|stop" >&2
        exit 3
        ;;
esac

```

---

### Post by VanderveckenSmith on 2013-04-07
The symlink is present, and the contents of /etc/init.d/rc.local contain the section you pasted.

---

### Post by kuifje09 on 2013-04-07
Are you sure rc.local is executable ?

Add some logging line to see if it is run anyway.  Maybe it is run but something else went wrong.
Have you checked your /var/log already?

---

### Post by VanderveckenSmith on 2013-04-07
It is executable.  Where in /var/log will I find the logging from rc.local?

---

### Post by VanderveckenSmith on 2013-04-07
I checked in boot.log.  It could not find /dev/zfs (even though t's there when I check after startup) and recommended I run sudo modprobe zfs, which I added to rc.local, and now it works.  Thanks!

---

