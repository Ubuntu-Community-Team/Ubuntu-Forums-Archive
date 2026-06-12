---
title: "Syntax error in script"
date: 2015-11-10
forum: General Help
---

### Post by zkab on 2015-11-10
I have followed the guidelines in [http://wiki.slimdevices.com/index.php/Debian_Package](http://wiki.slimdevices.com/index.php/Debian_Package) but get an strange syntax error
/etc/init.d/logitechmediaserver: 124: /etc/init.d/logitechmediaserver: Syntax error: "}" unexpected (expecting ")")

Here is my modified script ...

```
cat -n logitechmediaserver

     1	#!/bin/sh
     2	#
     3	# $Id$
     4	#
     5	# logitechmediaserver	initscript for slimserver.pl
     6	#			This file should be placed in /etc/init.d.
     7	#
     8	# Original Author: Mattias Holmlund
     9	#
    10	# Updated By: Dan Sully, Michael Herger
    11	
    12	#
    13	### BEGIN INIT INFO
    14	# Provides:          	logitechmediaserver
    15	# Required-Start:    	$all
    16	# Required-Stop:     	$all
    17	# Should-Start:      	$all
    18	# Should-Stop:       	$all
    19	# Default-Start:     	2 3 4 5
    20	# Default-Stop:      	0 1 6
    21	# Short-Description:	Startup script for the Logitech Media Server
    22	# Description:		Logitech Media Server powers the Squeezebox, Transporter and SLIMP3 network music \
    23	#			players and is the best software to stream your music to any software MP3 \
    24	#			player. It supports MP3, AAC, WMA, FLAC, Ogg Vorbis, WAV and more! \
    25	#			As of version 7.7 it also supports UPnP clients, serving pictures and movies too!"
    26	### END INIT INFO
    27	#
    28	
    29	set -e
    30	. /lib/lsb/init-functions
    31	
    32	PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin
    33	DESC="Logitech Media Server"
    34	NAME=squeezeboxserver
    35	NEWNAME=logitechmediaserver
    36	DAEMON=/usr/sbin/$NAME
    37	DAEMON_SAFE=/usr/sbin/${NAME}_safe
    38	PIDFILE=/var/run/$NEWNAME.pid
    39	SCRIPTNAME=/etc/init.d/$NEWNAME
    40	SLIMUSER=$NAME
    41	PREFSDIR=/var/lib/$NAME/prefs
    42	LOGDIR=/var/log/$NAME/
    43	CACHEDIR=/var/lib/$NAME/cache
    44	CHARSET=utf8
    45	SLIMOPTIONS=
    46	
    47	# Read config file if it is present.
    48	if [ -r /etc/default/$NEWNAME ]; then
    49		. /etc/default/$NEWNAME
    50	elif [ -r /etc/default/$NAME ]; then
    51		. /etc/default/$NAME
    52	fi
    53	
    54	#
    55	#	Function that starts the daemon/service.
    56	#
    57	d_start() {
    58	        # Use squeezeboxserver_safe to restart the daemon when
    59	        # it dies. This must be done to handle mysql restarts.
    60		start-stop-daemon --start --quiet \
    61	                --chuid $SLIMUSER \
    62	                --pidfile $PIDFILE \
    63			--exec $DAEMON_SAFE \
    64	                --background \
    65	                --make-pidfile \
    66	                -- \
    67	                $DAEMON \
    68	                --prefsdir $PREFSDIR \
    69	                --logdir $LOGDIR \
    70	                --cachedir $CACHEDIR \
    71			--charset=$CHARSET \
    72	                $SLIMOPTIONS
    73	}
    74	
    75	d_start_direct() {
    76		start-stop-daemon --start --quiet \
    77	                --chuid $SLIMUSER \
    78	                --pidfile $PIDFILE \
    79			--exec $DAEMON \
    80	                -- \
    81	                --pidfile $PIDFILE \
    82	                --daemon \
    83	                --prefsdir $PREFSDIR \
    84	                --logdir $LOGDIR \
    85	                --cachedir $CACHEDIR \
    86			--charset=$CHARSET \
    87	                $SLIMOPTIONS
    88	}
    89	
    90	#	Function that stops the daemon/service.
    91	#
    92	d_stop() {
    93	
    94		## This is a bug in the start-stop-daemon that checks the PID name from the /proc/PID/stat filesystem...
    95		## Unfortunately this cuts-off the name of the daemon because its longer now, and then it doesnt get 
    96		## caught by the start-stop-daemon. The daemon actually reports it as squeezeboxserve instead of 
    97		## squeezeboxserver_safe.
    98		start-stop-daemon --oknodo --stop --pidfile $PIDFILE --retry=TERM/30/KILL/5
    99	}
   100	
   101	#
   102	#	Function that sends a SIGHUP to the daemon/service.
   103	#
   104	d_reload() {
   105		start-stop-daemon --stop --quiet --pidfile $PIDFILE --signal 1
   106	}
   107	
   108	d_update() {
   109	       latest_lms=$(wget -q -O - "http://www.mysqueezebox.com/update/?version=7.9.0&revision=1&geturl=1&
   110	       lms_deb=$(echo $latest_lms|cut -d "/" -f8)
   111	       lms_new_Version=$(echo $lms_deb |cut -d "_" -f2)
   112	       installed_lms=$(dpkg-query -W -f '${status} ${package} ${version}\n'|grep logitech |cut -d " " -f
   113	       ls /sources/logi* -1t | tail -3| xargs -d '\n' rm -f
   114	       if [ ! $lms_new_Version = $installed_lms ]
   115	               then
   116	               echo 'Update Logitechmediaserver $installed_lms to $lms_newVersion'
   117	               mkdir -p /sources
   118	               cd /sources
   119	               wget $latest_lms
   120	               dpkg -i /sources/$lms_deb
   121	       else
   122	               echo "latest Version $lms_new_Version already installed"
   123	       fi
   124	}
   125	
   126	case "$1" in
   127	  start)
   128		echo -n "Making sure that $DESC is not running first: "
   129		d_stop
   130		echo -n "Starting $DESC"
   131		d_start
   132		echo "."
   133		;;
   134	  stop)
   135		echo -n "Stopping $DESC"
   136		d_stop
   137		echo "."
   138		;;
   139	  restart|force-reload)
   140		#
   141		#	If the "reload" option is implemented, move the "force-reload"
   142		#	option to the "reload" entry above. If not, "force-reload" is
   143		#	just the same as "restart".
   144		#
   145		echo -n "Restarting $NAME"
   146		d_stop
   147		d_start
   148		echo "."
   149		;;
   150	  status)  
   151		status_of_proc /usr/bin/$NEWNAME $NEWNAME
   152		;;
   153	 update)
   154	       d_stop
   155	       d_update
   156	       d_start 
   157	       ;; 
   158	
   159	  *)
   160		# echo "Usage: $SCRIPTNAME {start|stop|restart|force-reload|status}" >&2
   161		echo "Usage: $SCRIPTNAME {start|stop|restart|force-reload|update}" >&2
   162	
   163		exit 1
   164		;;
   165	esac
   166	
   167	exit 0
```

---

### Post by ajgreeny on 2015-11-10
So have you tried the script with a round bracket ) instead of the curly bracket } that you have used at line 124 of the script as the error says it expects?

---

### Post by zkab on 2015-11-10
Yes I have but then I get another error ...

sudo service logitechmediaserver update
/etc/init.d/logitechmediaserver: 168: /etc/init.d/logitechmediaserver: Syntax error: Unterminated quoted string

---

### Post by steeldriver on 2015-11-10
Unless the lines just got truncated when you posted, there are a bunch of incomplete command substitutions e.g.

```

109           latest_lms=**$(**wget -q -O - "http://www.mysqueezebox.com/update/?version=7.9.0&revision=1&geturl=1[COLOR=#ff0000]**&**[/COLOR]

```

```

112           installed_lms=**$(**dpkg-query -W -f '${status} ${package} ${version}\n'|grep logitech |cut -d " " [COLOR=#ff0000]**-f**[/COLOR]

```

---

### Post by zkab on 2015-11-10
Yes - you are right.
I found a backup script from a server and it said following ...

d_update() {
	latest_lms=$(wget -q -O - "http://www.mysqueezebox.com/update/?version=7.9.0&revision=1&geturl=1&os=deb")
	lms_deb=$(echo $latest_lms|cut -d "/" -f8)
	lms_new_Version=$(echo $lms_deb |cut -d "_" -f2)
	installed_lms=$(dpkg-query -W -f '${status} ${package} ${version}\n'|grep logitech |cut -d " " -f5)
	ls /sources/logi* -1t | tail -3| xargs -d '\n' rm -f
	if [ ! $lms_new_Version = $installed_lms ]
		then
		echo 'Update Logitechmediaserver $installed_lms to $lms_newVersion' 
		mkdir -p /sources
		cd /sources
		wget $latest_lms
		dpkg -i /sources/$lms_deb
	else
		echo "latest Version $lms_new_Version already installed"
	fi	
}

This worked OK - but I find it strange that Wiki for Squuezebox [http://wiki.slimdevices.com/index.php/Debian_Package](http://wiki.slimdevices.com/index.php/Debian_Package) gives an incorrect script.
Thanks again for your support.

---

