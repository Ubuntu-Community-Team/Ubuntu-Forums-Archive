---
title: "Move from 12.04 to 14.04 broke my init script"
date: 2014-06-27
forum: General Help
---

### Post by Rob_Brown on 2014-06-27
I recently moved my personal server onto new hardware and took the opportunity at that time to update from 12.04 to 14.04 (both LTS Server). All in all the move has not gone bady, I'm just struggling to get the last couple of things working.

On my old machine I had a script (rtorrent.conf) in /etc/init/ (C&P from somewhere or other and probably not the best way of doing this anyway) which contained the following:

```
description "ncurses BitTorrent client based on LibTorrent"


start on (local-filesystems and net-device-up and runlevel [2345])
stop on runlevel [016]


chdir /home/bro708


script
su bro708 -c "screen -d -m -S rtorrent rtorrent"
sleep 3
su bro708 -c "screen -d -m -S irssi irssi"
end script

```

This worked fine for me for over a year and started both rtorrent and irssi on boot every time.

I does not work however, on the new box. On rebooting the server ```
ps -aux | grep rtorrent
``` returns only one line for the grep process itself ```
bro708    9537  0.0  0.0   8588   920 pts/0    S+   12:50   0:00 grep --color=auto rtorrent
``` and the same happens for irssi.

If I manually run the script with ```
sudo start rtorrent
``` then rtorrent runs and I get ```
bro708    3923  0.0  0.0  26232  1300 ?        Ss   11:14   0:00 SCREEN -d -m -S rtorrent rtorrent
bro708    3945  3.7  7.0 414656 143648 pts/1   Ssl+ 11:14   3:39 rtorrent
bro708    9537  0.0  0.0   8588   920 pts/0    S+   12:50   0:00 grep --color=auto rtorrent
``` and similar for irssi.

Can anyone shed any light on why the script is not working at boot on the new machine? As I said at the start of this post, the script was a C&P from elsewhere anyway and I'm sure there's probably a better way of doing this, all I really want is for both programs to run as my user in my home directory on the new machine when it boots up...

Any help would be much appreciated, TIA.

---

### Post by Rob_Brown on 2014-06-27
Just a quick update, I solved the problem with irssi not starting even when the script was run manually, I'd used the wrong kind of "s it seems, I've edited the problem out of the initial post for clarity. So the script runs both programs now when started manually. I't just not working at boot, any suggestions?

---

### Post by Rob_Brown on 2014-06-28
I figured this out for myself and thought I'd put the solution here for posterity,

got some debugging enabled in my .conf script and screen was throwing an error on trying to start rtorrent saying it could not create /var/run/screen/, it transpires that this directory is created at boot by a job called screen-cleanup. On my Ubuntu 12.04 server I have an upstart script named /etc/init/screen-cleanup.conf which creates the screen directory and also a SysV process (/etc/init.d/screen-cleanup) which as far as I can tell simply calls the upstart script.

So on my old server I had screen-cleanup (set to start on filesystem) and also rtorrent/irssi (set to start on (local-filesystem and net-device-up and runlevel [2345])) all being started by upstart scripts held in /etc/init/ and it worked fine. On the new 14.04 system there is no screen-cleanup.conf in /etc/init/ and the screen-cleanup in /etc/init.d/ does the work directly and seemingly does not do so until after my upstart script has tried (and failed) to start rtorrent & irssi.

To cut a long story short the solution was to delete my upstart script at /etc/init/rtorrent.conf and create two SysV processes named rtorrent and irssi respectively in /etc/init.d/, I found a good one for rtorrent online [here]("https://github.com/mjsilva/rtorrent-screen-debian-init-script") and have bastardised it slightly and then adjusted it for irssi too, here's what they look like (obvioiusly you need to change the USER variable to the user name you wish the processes to run under):

rtorrent ...```
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
irssi ...```
#!/bin/bash### BEGIN INIT INFO
# Provides:          irssi
# Required-Start:    $local_fs $remote_fs $network $syslog
# Required-Stop:     $local_fs $remote_fs $network $syslog
# Default-Start:     2 3 4 5
# Default-Stop:      0 1 6
# Short-Description: Start/stop irssi daemon
### END INIT INFO


## Username to run irssi under
USER="<username>"


## Absolute path to the rtorrent binary.
IRSSI="/usr/bin/irssi"


## Absolute path to the screen binary.
SCREEN="/usr/bin/screen"


## Name of the screen session, you can then "screen -r irssi" to get it back
## to the forground and work with it on your shell.
SCREEN_NAME="irssi"


## Absolute path to irssi's PID file.
PIDFILE="/var/run/irssi.pid"


case "$1" in
    ## Start irssi in the background.
    start)
        echo "Starting irssi."
        start-stop-daemon --start --background --oknodo \
            --pidfile "$PIDFILE" --make-pidfile \
            --chuid $USER \
            --exec $SCREEN -- -DmUS $SCREEN_NAME $IRSSI
        if [[ $? -ne 0 ]]; then
            echo "Error: irssi failed to start."
            exit 1
        fi
        echo "irssi started successfully."
        ;;


    ## Stop irssi.
    stop)
        echo "Stopping irssi."
        start-stop-daemon --stop --oknodo --pidfile "$PIDFILE"
        if [[ $? -ne 0 ]]; then
            echo "Error: failed to stop irssi process."
            exit 1
        fi
        delete_socket
        echo "irssi stopped successfully."
        ;;


    ## Restart irssi.
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

Then I made them executable ...
```
sudo chmod +x /etc/init.d/rtorrent
sudo chmod +x /etc/init.d/irssi
```
... and activated them ...
```
sudo update-rc.d rtorrent defaults 99

sudo update-rc.d irssi defaults 99

```

Finally I rebooted to start the processes and rtorrent and irssi are both now running in detached screens under my user.

Hopefully this'll help out anyone else who runs into the same problem, it would seem to affect any attempt to run anything through screen via an upstart script...

---

