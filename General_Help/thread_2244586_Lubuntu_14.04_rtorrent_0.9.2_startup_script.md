---
title: "Lubuntu 14.04 rtorrent 0.9.2 startup script"
date: 2014-09-17
forum: General Help
---

### Post by apathia2 on 2014-09-17
I've been searching for weeks now trying to get rtorrent to start on boot. I've found many different scripts, but none of them seem to work. 

Right now, I've gotten as far as ```
cat: /home/servu/.rtorre: No such file or directorycannot find readable config /home/servu/.rtorre. check that it is there and permissions are appropriate

```

I'm using the init script from [http://libtorrent.rakshasa.no/downloads/rtorrent_init_script.sh](http://libtorrent.rakshasa.no/downloads/rtorrent_init_script.sh), with this code added to the top:
```
### BEGIN INIT INFO
# Provides:          rtorrent
# Required-Start:    $remote_fs $syslog
# Required-Stop:     $remote_fs $syslog
# Default-Start:     2 3 4 5
# Default-Stop:      0 1 6
# Short-Description: Start daemon at boot time
# Description:       Enable service provided by daemon. ### END INIT INFO
```
The permissions shouldn't be an issue (I changed it to 777 cause it was pissing me off). It is executable (sudo chmod +x /etc/init.d/rtorrent)

I used this to register the init file: sudo update-rc.d -f  rtorrent defaults

I've tried adding screen -fa -d -m rtorrent to /etc/rc.local

I've tried this script:
```
#!/bin/bash### BEGIN INIT INFO
# Provides:          rtorrent
# Required-Start:    $local_fs $remote_fs $network $syslog
# Required-Stop:     $local_fs $remote_fs $network $syslog
# Default-Start:     2 3 4 5
# Default-Stop:      0 1 6
# Short-Description: Start/stop rtorrent daemon
### END INIT INFO




## Username to run rtorrent under, make sure you have a .rtorrent.rc in the
## home directory of this user!
USER="<username>"




## Absolute path to the rtorrent binary.
RTORRENT="/usr/bin/rtorrent"




## Absolute path to the screen binary.
SCREEN="/usr/bin/screen"




## Name of the screen session, you can then "screen -r rtorrent" to get it back
## to the forground and work with it on your shell.
SCREEN_NAME="rtorrent"




## Absolute path to rtorrent's PID file.
PIDFILE="/var/run/rtorrent.pid"




## Absolute path to rtorrent's XMLRPC socket.
SOCKET="/var/run/rtorrent/rpc.socket"




## Check if the socket exists and if it exists delete it.
delete_socket() {
    if [[ -e $SOCKET ]]; then
        rm -f $SOCKET
    fi
}




case "$1" in
    ## Start rtorrent in the background.
    start)
        echo "Starting rtorrent."
        delete_socket
        start-stop-daemon --start --background --oknodo \
            --pidfile "$PIDFILE" --make-pidfile \
            --chuid $USER \
            --exec $SCREEN -- -DmUS $SCREEN_NAME $RTORRENT
        if [[ $? -ne 0 ]]; then
            echo "Error: rtorrent failed to start."
            exit 1
        fi
        echo "rtorrent started successfully."
        ;;




    ## Stop rtorrent.
    stop)
        echo "Stopping rtorrent."
        start-stop-daemon --stop --oknodo --pidfile "$PIDFILE"
        if [[ $? -ne 0 ]]; then
            echo "Error: failed to stop rtorrent process."
            exit 1
        fi
        delete_socket
        echo "rtorrent stopped successfully."
        ;;




    ## Restart rtorrent.
    restart)
        "$0" stop
        sleep 1
        "$0" start || exit 1
        ;;






    ## Print usage information if the user gives an invalid option.
    *)
        echo "Usage: $0 [start|stop|restart]"
        exit 1
        ;;




esac
```

I can manually run screen rtorrent or sudo screen rtorrent, and both work just fine, but when I try and use the scripts, nothing but errors.. Why?!?

---

### Post by ian-weisser on 2014-09-17
Usually because rtorrent requires a console (a DISPLAY environment variable), which is only assigned to a user at login (not at boot).
Without that DISPLAY variable, the process fails.

rtorrent isn't designed to run as a headless daemon at boot...but other torrent daemons (transmission, deluge) are.

---

### Post by apathia2 on 2014-09-17
So the solution is to what?

---

### Post by ian-weisser on 2014-09-17
Do you want your torrent client to start automatically at boot? Or at your login?

Do you want to autostart the torrent client's interface so you can see what's going on? Or are you satisfied with merely knowing that it's working?

Does it need to be rtorrent? Or are you willing to try another torrent client that maybe better suited to your answers above?

---

### Post by apathia2 on 2014-09-17
At boot, preferably. Just needs to be on, accessible via rutorrent.

---

### Post by apathia2 on 2014-09-22
So, anyone able to help with my little problem?

---

### Post by ian-weisser on 2014-09-22
Your problem isn't little.
You have rejected the best solutions already: Use a different torrent application, or start it at login instead of boot.

The only remaining solution is to use a terminal multiplexer like the 'screen' or 'tmux' applications. The additional complexity, however, introduces their own problems.

I ditched such a solution years ago in favor of deluge-daemon or transmission-daemon, both of which are trivial to autostart at boot.

---

### Post by apathia2 on 2014-09-22
I'm not sure why this is so difficult. The script is from the creators of rtorrent themselves. If it doesn't work, why is it there? I'm fairly certain there's a portion in the script that runs screen anyhow:
```
[COLOR=#000000]d_start() {[/COLOR]  [ -d "$base" ] && cd "$base"
  stty stop undef && stty start undef
  su -c "screen -ls | grep "\.${srnname}[[:space:]]" > /dev/null" $user || su -c "screen -dm -S $srnname" $user
  OLDIFS="$IFS"
  IFS=$'\n'
  if [ -z "$options" ] ; then
  	sleep 3
  	su -c "screen -S $srnname -X screen rtorrent" $user
  else
	  for option in $options ; do
  		sleep 3
		su -c "screen -S $srnname -X screen rtorrent $option" $user
	  done
  fi
  IFS="$OLDIFS"
}
```

Not to mention the countless other folk that have actually gotten it to work. It just seems that recent releases of ubuntu have caused some issues.

Right now the computer in question is only being used as a temporary pc, the login that's used doesn't have access to anything except basic programs and a web browser, so I'm fairly certain that running rtorrent under that user is pointless. I like rtorrent because of the features it comes with. It makes it easier for the other people that use it to actually use it. Deluge and Transmission are more advanced and thus, more difficult to use for basic users, so switching will probably result in a lot of hassle trying to get them to figure it out.

It's cool if you don't know how to get it to work, I'm sure someone here does..

---

### Post by ian-weisser on 2014-09-22
Did you install 'screen'? It's not included by default.

---

### Post by apathia2 on 2014-09-22
Yes, as mentioned in my first post, both "screen rtorrent" (from an admin account) and "sudo screen rtorrent" (to run as root) work fine.

---

### Post by ian-weisser on 2014-09-23
Okay, back to that post.

What about the error message?
Does the /home/servu/.rtorre file exist? Does it have proper permissions?

---

### Post by apathia2 on 2014-09-23
That's what I can't figure out, no where in any of my configs/scripts is there a /home/servu/.rtorre. It should be /home/servu/.rtorrent.rc, which has proper permissions (-rw-rw-rw- 1 servu servu 2751 Sep 22 23:25 /home/servu/.rtorrent.rc)

---

### Post by ian-weisser on 2014-09-24
Seems like a bug that should be reported to rtorrent.
Does it work if you create a symlink pointing to the correct file?

```
ln -s /home/servu/.rtorrent.rc /home/servu/.rtorre
```

---

### Post by apathia2 on 2014-09-24
"cannot find readable session directory /home/servu/.rtorre. check permissions"

---

### Post by ian-weisser on 2014-09-24
If you're running screen as root (not a good idea), then any child application should be looking in root's directory instead of yours for /home files.
So the error message is doubly confusing.

At this point, I'm out of ideas. Sorry.

---

### Post by apathia2 on 2014-09-24
Yeah it's messed up. Actually running as root (sudo screen rtorrent) works fine, but the start up script seems to be running something completely different..

---

### Post by sandyd on 2014-09-25
Side Note:
I noticed it as well in 14.04, before I switched to deluged.

Any screen command, either using upstart or init.d would not work properly, while they did in previous releases.

---

### Post by zero16 on 2014-11-12
You have to modify this script to make it work

Replace checkcnfg() function (originally located on line 57) with this simplified one:
```

checkcnfg() {
  session=$(cat "$config" | grep "^[[:space:]]*session" | sed "s/^[[:space:]]*session[[:space:]]*=[[:space:]]*//")
  if ! [ -r "$config" ] ; then
    echo "cannot find readable config $config. check that it is there and permissions are appropriate">&2
    exit 3
  elif ! [ -r "$session" ] ; then
    echo "cannot find readable session directory $config. check permissions">&2
    exit 3
  fi  
}

```

---

