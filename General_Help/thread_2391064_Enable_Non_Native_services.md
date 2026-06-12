---
title: "Enable Non Native services"
date: 2018-05-05
forum: General Help
---

### Post by SuperFreak on 2018-05-05
Is there a way to enable non native services in Ubuntu 18.04. I want to enable mmserver which I installed to start on boot before another service ,logitechmediaservice. The latter service is listed with the command 

```
systemctl status logitechmediaserver
```

and I can start mmserver with

```
systemctl start mmsever
```


but it will not start onn reboot  I don't see how to enable it which will allow it to start after every reboot

---

### Post by again? on 2018-05-06
systemctl start/stop are per session commands.
systemctl enable/disable are for loading @ boot.
Is mmserver enabled to start at boot?
```
systemctl is-enabled mmserver
```
[How To Use Systemctl to Manage Systemd Services and Units]("https://www.digitalocean.com/community/tutorials/how-to-use-systemctl-to-manage-systemd-services-and-units")

---

### Post by SuperFreak on 2018-05-06
mmserver cannot be enabled to start at boot. Or at least I haven't found out how. Thais what I would like to do.

From the command you gave I get:

```
$ systemctl is-enabled mmserver
mmserver.service is not a native service, redirecting to systemd-sysv-install.
Executing: /lib/systemd/systemd-sysv-install is-enabled mmserver
disabled

```

I will have a look at the link you mentioned, Thanks

---

### Post by again? on 2018-05-06
I'm not a systemd expert... just know a little from creating my own --user services to run a script and using plexmediaserver.
Not sure what "not a native service" means.

If "systemctl is-enabled mmserver" shows disabled,
what do you get when running...
```
systemctl enable mmserver
```

---

### Post by SuperFreak on 2018-05-06
```
$ systemctl enable mmserver
mmserver.service is not a native service, redirecting to systemd-sysv-install.
Executing: /lib/systemd/systemd-sysv-install enable mmserver
update-rc.d: error: mmserver Default-Start contains no runlevels, aborting.

```\


Unfortunately the instructions I used to install this service preceded 18.04 and systemd. With 16.04 I just installed Boot Up Manager and was able to edit the timing of the service and enable it quite easily. With systemd this no longer works

---

### Post by again? on 2018-05-06
OK, can't help much ... I'll leave it up to someone who knows more about systemd.

---

### Post by SuperFreak on 2018-05-06
Thanks

---

### Post by SuperFreak on 2018-05-07
anyone?

---

### Post by nlee2 on 2018-05-07
when mmserver is started, what is the output of

```
systemctl status mmserver
```

---

### Post by SuperFreak on 2018-05-07
Thanks for your reply. I have a dying HD on the machine in question and it may take a week or more to replace. I will try and answer your question when I get a chance.

---

### Post by SuperFreak on 2018-05-07
If I start mmserver first I get:

```
david@MainSqueeze:~$ sudo systemctl start mmserver.service
[sudo] password for david: 
david@MainSqueeze:~$ systemctl status mmserver
&#9679; mmserver.service
   Loaded: loaded (/etc/init.d/mmserver; generated)
   Active: active (exited) since Mon 2018-05-07 20:15:10 EDT; 3min 51s ago
     Docs: man:systemd-sysv-generator(8)
  Process: 2471 ExecStart=/etc/init.d/mmserver start (code=exited, status=0/SUCC

May 07 20:15:10 MainSqueeze systemd[1]: Starting mmserver.service...
May 07 20:15:10 MainSqueeze su[2472]: Successful su for david by root
May 07 20:15:10 MainSqueeze su[2472]: + ??? root:david
May 07 20:15:10 MainSqueeze su[2472]: pam_unix(su:session): session opened for u
May 07 20:15:10 MainSqueeze su[2472]: pam_unix(su:session): session closed for u
May 07 20:15:10 MainSqueeze systemd[1]: Started mmserver.service.
May 07 20:15:10 MainSqueeze mmserver[2471]: Running MusicMagicServer
lines 1-13/13 (END)


```

---

### Post by nlee2 on 2018-05-07
Thanks for the info. What is the output of

```
cat /etc/init.d/mmserver
```

---

### Post by SuperFreak on 2018-05-08
```
$ cat /etc/init.d/mmserver
#! /bin/sh

# NON-PRIVIELEGED USER TO RUN MUSICMAGICSERVER.
USER=david
# PATH TO THE MUSICMAGICMIXERSERVER 
export MUSICHOME=/home/david/MusicIP/

case $1 in
    start)
	su - $USER -c $MUSICHOME"MusicMagicServer start  & > /dev/null" 
	echo "Running MusicMagicServer"
	exit
	;;
    stop)
	su - $USER -c $MUSICHOME"MusicMagicServer stop  & > /dev/null" 
	echo "Stopped MusicMagicServer"
	exit
	;;
    *)
        echo "Usage: /etc/rc.d/init.d/mmserver { start | stop }"
	exit
	;;
esac



```

---

### Post by nlee2 on 2018-05-08
Try saving this in ~/.config/autostart/mmserver.desktop and reboot. Does this help?

```
[Desktop Entry]
Type=Application
Exec=sh -c "sudo systemctl start mmserver.service"
Hidden=false
NoDisplay=false
X-GNOME-Autostart-enabled=true
Name=mmserver
Comment=
```

---

### Post by SuperFreak on 2018-05-08
```
$ systemctl status mmserver
&#9679; mmserver.service
   Loaded: loaded (/etc/init.d/mmserver; generated)
   Active: inactive (dead)
     Docs: man:systemd-sysv-generator(8)
david@MainSqueeze:~$ systemctl enable mmserver
mmserver.service is not a native service, redirecting to systemd-sysv-install.
Executing: /lib/systemd/systemd-sysv-install enable mmserver
update-rc.d: error: mmserver Default-Start contains no runlevels, aborting.
david@MainSqueeze:~$ 

```

mmserver still does not seem to start nor am I able to ennable it. Do I need to mark the permissions of the file "executable"?

EDIT:marked file as executable and rebooted. No Joy

---

### Post by nlee2 on 2018-05-08
You need to visudo /etc/sudoers and allow user david to use sudo without password.

what is the output of

```
sudo cat /etc/sudoers
sudo id david
```

---

### Post by SuperFreak on 2018-05-08
> **nlee2 said:**
> You need to visudo /etc/sudoers and allow user david to use sudo without password.

what is the output of

```
sudo cat /etc/sudoers
sudo id david
```


Not comfortable running the PC without password protection

---

### Post by nlee2 on 2018-05-08
Try saving this in ~/.config/autostart/mmserver.desktop and reboot. Any better?

```
[Desktop Entry]
Type=Application
Exec=sh -c "/home/david/MusicIP/MusicMagicServer start  & > /dev/null"
Hidden=false
NoDisplay=false
X-GNOME-Autostart-enabled=true
Name=mmserver
Comment=
```

---

### Post by SuperFreak on 2018-05-08
That's great.
I now need it to start before another service called logitechmediaserver, which is a native enabled service.
I know of a script which will do a delayed  restart logitechmediaserver on boot, which might work.

---

### Post by nlee2 on 2018-05-08
Oops. Forgot to take care of dependencies. With logitechmediaserver.service started, what is the output of

```

systemctl status logitechmediaserver.service
```

---

### Post by SuperFreak on 2018-05-08
```
$ systemctl status logitechmediaserver.service















&#9679; logitechmediaserver.service - LSB: Startup script for the Logitech Media Server
   Loaded: loaded (/etc/init.d/logitechmediaserver; generated)
   Active: active (running) since Tue 2018-05-08 15:04:23 EDT; 1min 20s ago
     Docs: man:systemd-sysv-generator(8)
  Process: 2049 ExecStop=/etc/init.d/logitechmediaserver stop (code=exited, status=0/SUCCESS)
  Process: 2056 ExecStart=/etc/init.d/logitechmediaserver start (code=exited, status=0/SUCCESS)
    Tasks: 2 (limit: 4915)
   CGroup: /system.slice/logitechmediaserver.service
           &#9500;&#9472;2063 /bin/bash /usr/sbin/squeezeboxserver_safe /usr/sbin/squeezeboxserver --prefsdir /var/lib/squeezeboxserver/prefs --logdir /v
           &#9492;&#9472;2065 /usr/bin/perl /usr/sbin/squeezeboxserver --prefsdir /var/lib/squeezeboxserver/prefs --logdir /var/log/squeezeboxserver/ --c

May 08 15:04:23 MainSqueeze systemd[1]: Starting LSB: Startup script for the Logitech Media Server...
May 08 15:04:23 MainSqueeze logitechmediaserver[2056]: Making sure that Logitech Media Server is not running first: start-stop-daemon: warnin
May 08 15:04:23 MainSqueeze logitechmediaserver[2056]: No process in pidfile '/var/run/logitechmediaserver.pid' found running; none killed.
May 08 15:04:23 MainSqueeze logitechmediaserver[2056]: Starting Logitech Media Server.
May 08 15:04:23 MainSqueeze systemd[1]: Started LSB: Startup script for the Logitech Media Server.
~



```

Code seems to repeat over and over.
Got mmserver to start before logitechmediaserver on boot. Looks good

---

### Post by SuperFreak on 2018-05-08
Something has gone awry. Now mmserver doesn't seem to start and I get this error from logitechmediaserver

```
$ systemctl start logitechmediaserver.service
david@MainSqueeze:~$ systemctl enable logitechmediaserver.service
logitechmediaserver.service is not a native service, redirecting to systemd-sysv-install.
Executing: /lib/systemd/systemd-sysv-install enable logitechmediaserver
Failed to reload daemon: Method call timed out

```

I created local.rc in etc with this script
```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.



sleep 3;sudo /etc/init.d/logitechmediaserver restart

exit 0
```

It worked for a couple of boots and now I get the error message at top and mmsever doesn't seem to run

---

### Post by SuperFreak on 2018-05-08
I deleted the 3 files I created rc.local, rc-local.service and rc.local.service that were used to restart logitechmediaserver so mmserver effectively started before logitechmediaserver. Now mmserver works but unfortunately not before logitechmediaserver

---

### Post by SuperFreak on 2018-05-09
@nlee2

I know you are probably irritated that I put those scripts in but they are removed now and it is back the way you had it for me. I just need to set up logitechmediaserver so either it restarts after mmserver or just does start until after mmserver. Can you help with this? I greatly appreciate the help you have given me so far.

---

### Post by nlee2 on 2018-05-09
No problem. It is a good thing that you experiment with your ideas on how to get things running just the way that you like. It is not just once or twice that I shot myself in the foot.

What is the output of

```
cat /etc/init.d/logitechmediaserver
```

---

### Post by SuperFreak on 2018-05-09
```
$ cat /etc/init.d/logitechmediaserver
#!/bin/sh
#
# $Id$
#
# logitechmediaserver	initscript for slimserver.pl
#			This file should be placed in /etc/init.d.
#
# Original Author: Mattias Holmlund
#
# Updated By: Dan Sully, Michael Herger

#
### BEGIN INIT INFO
# Provides:          	logitechmediaserver
# Required-Start:    	$all
# Required-Stop:     	$all
# Should-Start:      	$all
# Should-Stop:       	$all
# Default-Start:     	2 3 4 5
# Default-Stop:      	0 1 6
# Short-Description:	Startup script for the Logitech Media Server
# Description:		Logitech Media Server powers the Squeezebox, Transporter and SLIMP3 network music \
#			players and is the best software to stream your music to any software MP3 \
#			player. It supports MP3, AAC, WMA, FLAC, Ogg Vorbis, WAV and more! \
#			As of version 7.7 it also supports UPnP clients, serving pictures and movies too!"
### END INIT INFO
#

set -e
. /lib/lsb/init-functions

PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin
DESC="Logitech Media Server"
NAME=squeezeboxserver
NEWNAME=logitechmediaserver
DAEMON=/usr/sbin/$NAME
DAEMON_SAFE=/usr/sbin/${NAME}_safe
PIDFILE=/var/run/$NEWNAME.pid
SCRIPTNAME=/etc/init.d/$NEWNAME
SLIMUSER=$NAME
PREFSDIR=/var/lib/$NAME/prefs
LOGDIR=/var/log/$NAME/
CACHEDIR=/var/lib/$NAME/cache
CHARSET=utf8

## if you want to add additional options
## use /usr/sbin/squeezeboxserver --help 
## for the supported options and place them
## into the configfile  /etc/default/logitechmediaserver


# Read config file if it is present.
if [ -r /etc/default/$NEWNAME ]; then
	. /etc/default/$NEWNAME
elif [ -r /etc/default/$NAME ]; then
	. /etc/default/$NAME
fi

#
#	Function that starts the daemon/service.
#
d_start() {
        # Use squeezeboxserver_safe to restart the daemon when
        # it dies. This must be done to handle mysql restarts.
	start-stop-daemon --start --quiet \
                --chuid $SLIMUSER \
                --pidfile $PIDFILE \
		--exec $DAEMON_SAFE \
                --background \
                --make-pidfile \
                -- \
                $DAEMON \
                --prefsdir $PREFSDIR \
                --logdir $LOGDIR \
                --cachedir $CACHEDIR \
		--charset=$CHARSET \
                $SLIMOPTIONS
}

d_start_direct() {
	start-stop-daemon --start --quiet \
                --chuid $SLIMUSER \
                --pidfile $PIDFILE \
		--exec $DAEMON \
                -- \
                --pidfile $PIDFILE \
                --daemon \
                --prefsdir $PREFSDIR \
                --logdir $LOGDIR \
                --cachedir $CACHEDIR \
		--charset=$CHARSET \
                $SLIMOPTIONS
}

#	Function that stops the daemon/service.
#
d_stop() {

	## This is a bug in the start-stop-daemon that checks the PID name from the /proc/PID/stat filesystem...
	## Unfortunately this cuts-off the name of the daemon because its longer now, and then it doesnt get 
	## caught by the start-stop-daemon. The daemon actually reports it as squeezeboxserve instead of 
	## squeezeboxserver_safe.
	start-stop-daemon --oknodo --stop --pidfile $PIDFILE --retry=TERM/30/KILL/5
}

#
#	Function that sends a SIGHUP to the daemon/service.
#
d_reload() {
	start-stop-daemon --stop --quiet --pidfile $PIDFILE --signal 1
}

case "$1" in
  start)
	echo -n "Making sure that $DESC is not running first: "
	d_stop
	echo -n "Starting $DESC"
	d_start
	echo "."
	;;
  stop)
	echo -n "Stopping $DESC"
	d_stop
	echo "."
	;;
  restart|force-reload)
	#
	#	If the "reload" option is implemented, move the "force-reload"
	#	option to the "reload" entry above. If not, "force-reload" is
	#	just the same as "restart".
	#
	echo -n "Restarting $NAME"
	d_stop
	d_start
	echo "."
	;;
  status)  
	status_of_proc /usr/bin/$NEWNAME $NEWNAME
	;;
  *)
	echo "Usage: $SCRIPTNAME {start|stop|restart|force-reload|status}" >&2
	exit 1
	;;
esac

exit 0

```

---

### Post by nlee2 on 2018-05-09
1. Make a copy of /etc/init.d/mmserver
2. Move ~/.config/autostart/mmserver.desktop to another folder
3. Save the following in /etc/init.d/mmserver
4. systemctl daemon-reload
5. systemctl enable mmserver
6. if no errors then reboot

```
#! /bin/sh

#
### BEGIN INIT INFO
# Provides:              mmserver
# Required-Start:        $all
# Required-Stop:         $all
# Should-Start:          $all
# Should-Stop:           $all
# Default-Start:         2 3 4 5
# Default-Stop:          0 1 6
# Short-Description:    Startup script for mmserver
# Description:        
### END INIT INFO

# NON-PRIVIELEGED USER TO RUN MUSICMAGICSERVER.
USER=david
# PATH TO THE MUSICMAGICMIXERSERVER 
export MUSICHOME=/home/david/MusicIP/

case $1 in
    start)
    su - $USER -c $MUSICHOME"MusicMagicServer start  & > /dev/null" 
    echo "Running MusicMagicServer"
    exit
    ;;
    stop)
    su - $USER -c $MUSICHOME"MusicMagicServer stop  & > /dev/null" 
    echo "Stopped MusicMagicServer"
    exit
    ;;
    *)
        echo "Usage: /etc/rc.d/init.d/mmserver { start | stop }"
    exit
    ;;
esac
```

---

### Post by SuperFreak on 2018-05-09
I replaced the script in mmserver with the one you provided.

```
$ systemctl daemon-reload
david@MainSqueeze:~$ systemctl enable mmserver
mmserver.service is not a native service, redirecting to systemd-sysv-install.
Executing: /lib/systemd/systemd-sysv-install enable mmserver
update-rc.d: error: no runlevel symlinks to modify, aborting!

```

---

### Post by nlee2 on 2018-05-09
update-rc.d mmserver defaults
systemctl daemon-reload
systemctl enable mmserver

---

### Post by SuperFreak on 2018-05-09
```
~$ update-rc.d mmserver defaults
david@MainSqueeze:~$ systemctl daemon-reload
david@MainSqueeze:~$ systemctl enable mmserver
mmserver.service is not a native service, redirecting to systemd-sysv-install.
Executing: /lib/systemd/systemd-sysv-install enable mmserver
update-rc.d: error: no runlevel symlinks to modify, aborting!
```

Perhaps my ignorance of how the script works but is it starting and stopping mmserver. I want mmserver to start and logitechmediaserver to restart onbooting up the computer.
Sorry if I am not understanding

---

### Post by nlee2 on 2018-05-09
> **SuperFreak said:**
>  I want mmserver to start and logitechmediaserver to restart onbooting up the computer.


These are the 2 scripts that should run on boot. 
/etc/init.d/mmserver
/etc/init.d/logitechmediaserver 

logitechmediaserver is enabled to run on boot. Unfortunately there is a problem to enable mmserver to run on boot due to errors in upstart. Possible solutions are to 

1. fix mmserver errors in upstart.
2. convert mmserver and logitechmediaserver to systemd units <=====best
3. autostart mmserver and logitechmediaserver when user david login

What is the output of

```
find /etc/rc*.d -name *logitechmediaserver*
find /etc/rc*.d -name *mmserver*

```

If you get a hit then the output of

ls -la filenameofresultfromabove

---

### Post by SuperFreak on 2018-05-09
```
david@MainSqueeze:~$ find /etc/rc*.d -name *logitechmediaserver*
/etc/rc0.d/K01logitechmediaserver
/etc/rc1.d/K01logitechmediaserver
/etc/rc2.d/S01logitechmediaserver
/etc/rc3.d/S01logitechmediaserver
/etc/rc4.d/S01logitechmediaserver
/etc/rc5.d/S01logitechmediaserver
/etc/rc6.d/K01logitechmediaserver
david@MainSqueeze:~$ ls -la K01logitechmediaserver
ls: cannot access 'K01logitechmediaserver': No such file or directory
david@MainSqueeze:~$ ls -la /etc/rc0.d/K01logitechmediaserver
lrwxrwxrwx 1 root root 29 Apr 26 20:43 /etc/rc0.d/K01logitechmediaserver -> ../init.d/logitechmediaserver
david@MainSqueeze:~$ ls -la /etc/rc1.d/K01logitechmediaserver
lrwxrwxrwx 1 root root 29 Apr 26 20:43 /etc/rc1.d/K01logitechmediaserver -> ../init.d/logitechmediaserver
david@MainSqueeze:~$ ls -la /etc/rc2.d/S01logitechmediaserver
lrwxrwxrwx 1 root root 29 Apr 26 20:43 /etc/rc2.d/S01logitechmediaserver -> ../init.d/logitechmediaserver
david@MainSqueeze:~$ ls -la /etc/rc3.d/S01logitechmediaserver
lrwxrwxrwx 1 root root 29 Apr 26 20:43 /etc/rc3.d/S01logitechmediaserver -> ../init.d/logitechmediaserver
david@MainSqueeze:~$ ls -la /etc/rc4.d/S01logitechmediaserver
lrwxrwxrwx 1 root root 29 Apr 26 20:43 /etc/rc4.d/S01logitechmediaserver -> ../init.d/logitechmediaserver
david@MainSqueeze:~$ ls -la /etc/rc5.d/S01logitechmediaserver
lrwxrwxrwx 1 root root 29 Apr 26 20:43 /etc/rc5.d/S01logitechmediaserver -> ../init.d/logitechmediaserver
david@MainSqueeze:~$ ls -la /etc/rc6.d/K01logitechmediaserver
lrwxrwxrwx 1 root root 29 Apr 26 20:43 /etc/rc6.d/K01logitechmediaserver -> ../init.d/logitechmediaserver
david@MainSqueeze:~$ find /etc/rc*.d -name *mmserver*
david@MainSqueeze:~$ 



```

---

### Post by nlee2 on 2018-05-09
```

ln -s /etc/init.d/mmserver /etc/rc0.d/K01mmserver 
ln -s /etc/init.d/mmserver /etc/rc1.d/K01mmserver 
ln -s /etc/init.d/mmserver /etc/rc2.d/S01mmserver 
ln -s /etc/init.d/mmserver /etc/rc3.d/S01mmserver 
ln -s /etc/init.d/mmserver /etc/rc4.d/S01mmserver 
ln -s /etc/init.d/mmserver /etc/rc5.d/S01mmserver 
ln -s /etc/init.d/mmserver /etc/rc6.d/K01mmserver 
systemctl daemon-reload
systemctl enable mmserver
reboot

```

---

### Post by SuperFreak on 2018-05-09
I think it worked.

I have to go out but I will test it more fully as soon as possible.
Many Thanks

---

### Post by SuperFreak on 2018-05-10
@nlee2

I wanted to tell you that the help you gave me works fine. I have tried a few reboots and it works perfectly. I also wanted you to know what this was for. Logitechmediaserver is open source software used to run music collections on the Squeezebox, Radio and Touch family of hardware which works wirelessly or wired to a server (ie my PC) holding a music collection and plays the music back through a stereo or it's own speaker (ie the squeezebox radio). mmserver is part of MusicIP which creates playlists for in this case Logitechmediaserver based on a seed track selecting similar tracks of music and uses some kind of algorithm to select tracks based on the seed track). MusicIP is abandonware and it is an uphill battle getting it to work with each LTS of Ubuntu.

I am very grateful and with your permission I would like to post the steps to get it to work on Logitech's user forum [https://forums.slimdevices.com](https://forums.slimdevices.com)


Thanks again

---

### Post by nlee2 on 2018-05-10
Glad that it worked out for you. You have my go ahead to post with the usual disclaimer that I am off the hook for anything.

---

### Post by SuperFreak on 2018-05-13
@nlee2
This is a link to what I put on the thread [https://forums.slimdevices.com/showthread.php?108991-MusicIP-on-Ubuntu-18-04&p=913569#post913569]("https://forums.slimdevices.com/showthread.php?108991-MusicIP-on-Ubuntu-18-04&p=913569#post913569")

---

