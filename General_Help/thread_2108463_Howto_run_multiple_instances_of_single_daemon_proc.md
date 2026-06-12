---
title: "Howto run multiple instances of single daemon process??"
date: 2013-01-24
forum: General Help
---

### Post by dazz100 on 2013-01-24
Hello
I am attempting to setup a remote headless server with a webcam application using Motion.  This will have two cameras.
Motion is designed to run as a daemon controlling multiple cameras.  Motion has a bug which prevents a single instance of Motion running multiple cameras.  This bug is reported on Launchpad 604169.

The work around is to run an instance of Motion for each camera.  This can be done from the command line
>  motion -c conf1 && motion -c conf2
where conf1 and conf2 are configuration files for each camera.

The question I have is how can Ubuntu be configured to launch these two instances as daemons.  The init.d script only seems to check for one instance.   If one instance of Motion stops, the init.d script doesn't appear to be able to sense that and restart a 2nd Motion with the right config file.

the relevant part of the init.d/motion script is:
```
case "$1" in
  start)
    if check_daemon_enabled ; then
        log_daemon_msg "Starting motion detection daemon : $NAME"
        ### BEGIN /var/run Fix
        if ! [ -d /var/run/motion ]; then
       mkdir -p /var/run/motion
        fi
   chown root:motion /var/run/motion
   chmod 775 /var/run/motion

        ### END /var/run Fix
   log_daemon_msg "Starting $DESC" "$N
...
```


I need a solution that will ensure that the two Motion instances are kept running.  An acceptable solution would be that if one instance died, then kill the remaining one and restart both (to ensure both config files are correctly specified). Typically the reason Motion dies is because of some disturbance (eg. power failure).

This is the first time I have had to dive into the nuts and bolts of running daemons.  I am assuming that I will need to edit the init.d/motion script but I don't know how to sense if two instances are running or restart them.

Any suggestions please?

Dazz

---

### Post by dazz100 on 2013-01-27
Hi
I think I have found the solution here:
[http://ubuntuforums.org/showthread.php?t=1497376]("http://ubuntuforums.org/showthread.php?t=1497376")

Dazz

---

### Post by HiImTye on 2013-01-27
yeah, it needs to know the PID of the one that crashes, so add a PID file to each daemon and have it run a check against the PID and you should be golden

---

### Post by dazz100 on 2013-01-29
Hello

The program I am running is Motion.  It is supposed to be able to run multiple threads (one for each camera) But that feature doesn’t work.  
Motion reads from a config file normally located at /etc/motion/motion.conf.
Motion accepts a command line argument specifying al alternative location.

The Motion software doesn’t run root, it runs as a user “motion”.
Issues with permissions relate to the PID file directory “/var/run/” means I have to create a subdirectory “/var/run/motion” with permissions for the “motion” user to write the PID file.

So with that bit of back ground I need to get two instances of Motion running.

To achieve that I have

Created the directory “/etc/motion2/” containing the relevant config file
Created the directory “/var/run/motion2” to store the PID file
Copied and modified /etc/init.d/motion2 the start stop restart script for the 2nd instance.
Copied and created a motion2 file in "/etc/defaults/"
Created a synlink  “/usr/bin/motion2”  pointing to the executable “/usr/bin/motion”

In summary for each thread I have

Motion    
> Config    :    /etc/motion/motion.conf
PID       :   /var/run/motion/
Executable:   /usr/bin/motion           

Motion2
> Config    :      /etc/motion2/motion2.conf
PID       :             /var/run/motion2/
Executable:             /usr/bin/motion2

A listing of the “/usr/bin/” dir gives:
> -rwxr-xr-x 1 root   root     223228 Mar  3  2012 motion
lrwxrwxrwx 1 root   root          6 Jan 28 22:36 motion2 -> motion
A $ ps –A | grep motion
Will return the correct motion or motion2 for the instance running.

I know that I didn’t need to create the motion2 directories.  I could have configured all of this in the existing directories.
Separating the directories will make it easier for me to remember what I did when I come back to maintain the system in the future.

The result is that I can run each instance individually as a daemon.  Each instance loads the correct config file, stores the right PID file in the right place and runs happlily.
The problem is that when I try and start a 2nd instance, I get the response that the daemon is already running.  It doesn’t matter whether I start Motion or Motion2 first, I get the same response.

It seems that the test applied by “start-stop-daemon” is ignoring PIDs and process names.
Excerpts of the “/etc/init.d/” scripts are shown below.

The init.d script for the motion instance is:
> NAME=motion
PATH_BIN=/bin:/usr/bin:/sbin:/usr/sbin
DAEMON=/usr/bin/motion
PIDPATH=/var/run/motion
PIDFILE=/var/run/motion/$NAME.pid
DEFAULTS=/etc/default/$NAME
DESC="motion detection daemon"

ENV="env -i LANG=C PATH=$PATH_BIN"

. /lib/lsb/init-functions

…..

case "$1" in
  start)
    if check_daemon_enabled ; then
        log_daemon_msg "Starting motion detection daemon : $NAME"
        ### BEGIN /var/run Fix
        if ! [ -d $PIDPATH ]; then
 		mkdir -p $PIDPATH
        fi
	chown root:motion $PIDPATH
	chmod 775 $PIDPATH

        ### END /var/run Fix
	log_daemon_msg "Starting $DESC" "$NAME" 
#this next line won’t start motion if motion2 is running.
if start-stop-daemon --start --oknodo --exec $DAEMON -b --chuid motion ; then
            log_end_msg 0
        else
            log_end_msg 1
            RET=1
        fi
    fi
    ;;

The init.d script for the motion2 instance is:

> NAME=motion2
PATH_BIN=/bin:/usr/bin:/sbin:/usr/sbin
DAEMON=/usr/bin/motion2
DAEMONARGS=" -c /etc/motion2/motion2.conf"
PIDPATH=/var/run/motion2
PIDFILE=/var/run/motion2/$NAME.pid
DEFAULTS=/etc/default/$NAME
DESC="motion2 detection daemon"

ENV="env -i LANG=C PATH=$PATH_BIN"

. /lib/lsb/init-functions

…..

case "$1" in
  start)
    if check_daemon_enabled ; then
        log_daemon_msg "Starting motion detection daemon : $NAME"
        ### BEGIN /var/run Fix
        if ! [ -d "$PIDPATH" ]; then
 		mkdir -p "$PIDPATH"
        fi
	chown root:motion "$PIDPATH"
	chmod 775 "$PIDPATH"

        ### END /var/run Fix
	log_daemon_msg "Starting $DESC" "$NAME" 
#this next line won’t start motion2 if motion is running.
if start-stop-daemon --start --oknodo --exec $DAEMON -b --chuid motion --$DAEMONARGS; then
            log_end_msg 0
        else
            log_end_msg 1
            RET=1
        fi
    fi
    ;;

So I can’t figure out what I am doing wrong.  I can’t get the two instances running at the same time.  It's a mystery to me.

I am wondering if I need to add matching args to the start-stop-daemon command?  

Dazz

---

### Post by SeijiSensei on 2013-01-29
Is the "daemon" mode designed so you can connect to the program over the network and watch the video?  If so, then you would need to run the two daemon processes on separate "ports."  I have no idea how you would do that, though.  Maybe you can control this in the .conf file?

That may not be the reason why you can't run a second instance, but it's a possibility.

---

### Post by dazz100 on 2013-01-29
Hi
The Motion program can send video over the network.  It also has a specific setup mode that allows settings in the config file to be changed on the fly.  The port addresses are user set so two instances won't clash.  I have no plans to permanently send out video.  My intention is to capture images, then use other programs to send them out to an ftp server.

I have been doing some more reading and I think my problem is that I need to change filters from exec to something else (say PIDfile or name). I suspect that the exec filter is seeing the actual process (motion) rather than the synlink.  

Motion creates valid PID files so I will try that.

Edit: I found this link [start-stop-daemon to create multiple instances of executable through upstart]("http://datum-bits.blogspot.com/2011/09/start-stop-daemon-to-create-multiple.html#!/2011/09/start-stop-daemon-to-create-multiple.html") which talks about what I want to do.



Dazz

---

### Post by dazz100 on 2013-01-30
Hi

I added a  "--name $NAME" to the start command (no other changes) and this worked.  It allowed me to individually start separate instances of the daemon.

Where it failed was on the stop command.  Running stop killed either or both instances.
The solution was to add the same “--name $NAME” argument to the restart/stop commands.

It all works now.

Dazz

---

### Post by dazz100 on 2013-02-07
Hi

The 2nd instance would not automatically start after a reboot.
To fix this problem I added sym links to the rc<x>.d directories.  
These sym links point to the script in the init.d directory.
I just used the existing sym links for motion to create the links for motion 2.


Dazz

---

