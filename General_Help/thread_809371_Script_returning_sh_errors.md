---
title: "Script returning sh errors"
date: 2008-05-27
forum: General Help
---

### Post by Pyromanci on 2008-05-27
I have a script I have been trying to make. Right now it is just a manual execution but sooner. I do want it to run on the machine startup as well.

When I execute the script it return the following:
```
-bash: root/vlc: /bin/sh^M: bad interpreter: No such file or directory
```

Here is my script:
```
#!/bin/sh

set -e

. /lib/lsb/init-functions

DAEMON=/usr/bin/vlc
EXDAEMON=/usr/bin/vlc $2 -L

test -x $DAEMON || exit 0

case "$1" in
  start)
    log_begin_msg "Starting VLC Media Player"
    start-stop-daemon --start --background -m --pidfile /var/run/vlc.pid --exec $EXDAEMON && log_end_msg 0 || log_end_msg 1
    ;;
  stop)
    log_begin_msg "Stopping VLC Media Player"
    start-stop-daemon --stop --pidfile /var/run/vlc.pid --oknodo --exec $DAEMON && log_end_msg 0 || log_end_msg 1
    rm -f /var/run/vlc.pid
    ;;
  restart)
    $0 stop
    $0 start
    ;;
  *)
    log_success_msg "Usage: vlc {start|stop|restart}"
    exit 1
    ;;
esac

exit 0

```

Anyone see what I have done wrong?

---

### Post by Monicker on 2008-05-27
"/bin/sh^M"


How was the file created?  It looks like you managed to put a control character in that line, which is keeping it from finding the proper interpreter.

---

### Post by Pyromanci on 2008-05-27
I typed it all out in a program called Crimson Editor on my desktop. then inside a ssh window i created the file with the editor command and just pasted the script in line by line.

---

### Post by ibuclaw on 2008-05-27
Hmm... Looks like you created a DOS file in a UNIX environment...

Make a backup of the file, and run this command in the file location.
```
sed -i -e 's/^M$//g' scriptname.sh
```
where scriptname.sh is the name of the file.

Regards
Iain

---

### Post by Pyromanci on 2008-05-27
Ty that works, but now there other problem related to vlc, but i will take those to the vlc forums.

---

### Post by ibuclaw on 2008-05-27
And if you are curious as to how to reverse it. (Re-produce the error you got)

```
sed -i -e "s/$/`echo -e \\\r`/g" scriptname.sh
```

Regards
Iain

---

