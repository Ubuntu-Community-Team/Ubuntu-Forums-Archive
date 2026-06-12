---
title: "Timidity problem"
date: 2008-06-16
forum: General Help
---

### Post by Zoja on 2008-06-16
i get sudo apt-get update nothing happens 
and when i get sudo apt-get upgrade i get an error which i get with every update available ..

```
 * Starting TiMidity++ ALSA midi emulation...                            [fail] 
invoke-rc.d: initscript timidity, action "start" failed.

E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by iaculallad on 2008-06-16
On your terminal:

```
sudo apt-get -f install
sudo apt-get update && sudo apt-get upgrade

```

---

### Post by Zoja on 2008-06-16
nope , the same thing
```
Konfigurowanie timidity (2.13.2-19ubuntu1) ...
 * Starting TiMidity++ ALSA midi emulation...                            [fail] 
invoke-rc.d: initscript timidity, action "start" failed.
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

This is my timidity at /etc/init.d/timidity

```
#!/bin/sh
#
# TiMidity      /etc/init.d/ initscript for TiMidity++
#               $Id: timidity.init,v 1.6 2004/09/30 01:04:04 hmh Exp $
#
#               Copyright (c) 2004 by Henrique M. Holschuh <hmh@debian.org>
#               Copyright (c) 2007 Joost Yervante Damad <andete@debian.org>
#
#               Distributed under the GPL version 2
#

### BEGIN INIT INFO
# Provides: timidity
# Required-Start: $remote_fs
# Required-Stop: $remote_fs
# Default-Start:  2 3 4 5
# Default-Stop: 0 1 6
# Short-Description: start and stop timidity
# Description:  TiMidity++ is a very high quality software-only MIDI sequencer
#        and MOD player.
### END INIT INFO

. /lib/lsb/init-functions

NAME="timidity"
PATH=/sbin:/bin:/usr/sbin:/usr/bin
DAEMON=/usr/bin/${NAME}
DESC="TiMidity++ ALSA midi emulation"
PMIDI=/usr/bin/pmidi
PIDFILE=/var/run/${NAME}.pid

set -e

test -x ${DAEMON} || exit 0
test -x ${PMIDI} && pmidi_enabled="true" || pmidi_enabled="false";

TIM_ALSASEQ=
TIM_ALSASEQPARAMS="-B2,8"
[ -r /etc/default/timidity ] && . /etc/default/timidity
if [ "${TIM_ALSASEQ}" != "true" ]; then
	echo "Timidity is not yet configured." >&2
	echo "Enable Alsa Sequencer first by editing /etc/default/timidity." >&2
	exit 0
fi
PARAMS="${TIM_ALSASEQPARAMS} -iAD"

START="--start --quiet --exec ${DAEMON} --pidfile ${PIDFILE} -- ${PARAMS}"

case "$1" in
  start)
	#log_daemon_msg "Starting" "${NAME}"
	[ -d /proc/asound ] || {
		log_end_msg 1
  		log_warning_msg "ALSA is not active, cannot start $DESC"
		exit 0
	}
	log_begin_msg "Starting $DESC..."
	if start-stop-daemon ${START} >/dev/null; then
		log_end_msg 0
  		#if [ $pmidi_enabled = "true" ] ; then
  		#	sleep 1
  		#	echo -n "Emulating midi on ports: ";
		#	pmidi -l | grep "TiMidity" | cut -f 1 -d ' ' | xargs
		#fi
	else
		log_end_msg 1
		exit 1
		#if start-stop-daemon --test ${START}  >/dev/null 2>&1; then
		#	echo "(failed)."
		#	exit 1
		#else
		#	echo "already running."
		#	exit 0
		#fi
	fi
	;;
  stop)
	log_begin_msg "Stopping $DESC..."
	if start-stop-daemon --stop --quiet --oknodo --pidfile ${PIDFILE} \
          --name $(basename ${DAEMON}) --retry 10 ; then
		log_end_msg 0
	else
		log_end_msg 1
		exit 1
	fi
	;;
  restart|force-reload)
  	$0 stop
	exec $0 start
  	;;
  *)
    echo "Usage: $0 {start|stop|restart|force-reload}" >&2
    exit 1
esac
 
exit 0
```

---

### Post by iaculallad on 2008-06-16
Stop timidity manually:

```
sudo killall timidity
sudo apt-get install
```

---

### Post by Zoja on 2008-06-16
the same thing happens :/

---

### Post by jukingeo on 2008-06-17
> **Zoja said:**
> the same thing happens :/

I have a similar timidity problem.  I had a problem with Pulse Audio and OSS in regards to a guide I followed to restore a streaming audio problem I had.  That guide blew out my sound completely so I was forced to uninstall both Pulse and OSS.  The trouble is now I get an error message when trying to reinstall OSS.

This is the latter part of my reinstallation process of OSS within my Terminal:

nvoke-rc.d: initscript timidity, action "start" failed.
dpkg: error processing timidity (--configure):
subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of ubuntustudio-audio:
ubuntustudio-audio depends on timidity; however:
Package timidity is not configured yet.
dpkg: error processing ubuntustudio-audio (--configure):
dependency problems - leaving unconfigured
Errors were encountered while processing:
timidity
ubuntustudio-audio
E: Sub-process /usr/bin/dpkg returned an error code (1)

Now I understand that timidity has something to do with MIDI and I know I will need it, but as of now it is preventing an install of OSS.  Without OSS I don't have sound.

So any assistance in resolving this matter would be appreciated.

Thank You

---

### Post by alphonce on 2008-06-17
I got it properly configured when I started the recovery mode and then choosed "repair broken packages", then just start as normal and timidity should be configured.

---

### Post by jukingeo on 2008-06-17
> **alphonce said:**
> I got it properly configured when I started the recovery mode and then choosed "repair broken packages", then just start as normal and timidity should be configured.

I ended up going into Synaptic, finding Timidity and did a "remove all".  I know that my bite me in the a-- in the future, but I was able to continue my reinstallation of OSS

---

