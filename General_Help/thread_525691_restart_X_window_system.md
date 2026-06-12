---
title: "restart X window system"
date: 2007-08-14
forum: General Help
---

### Post by chanman on 2007-08-14
When I do a cold boot on my laptop (Asus A8Js), Gnome starts fine. But of I log out or Ctrl+Alt+Backspace and try to log back in, It just stalls for a minute then a white block pops up on the upper left side of the screen. Then nothing else happens. I can still restart X and can get into the failsafe terminal mode. I have to reboot my computer in order to get back into Gnome.

This happens with or without compiz. With or without auto login.

---

### Post by tribble222 on 2007-08-14
I'm not an expert, but maybe something is wrong with your gdm init file?  Does the command "sudo /etc/init.d/gdm restart" let you log in to gnome?  I'm not sure if you're seeing a login screen at all after you ctrl-alt-backspace.

---

### Post by bjarneh on 2007-08-14
ctrl+alt+backspace is not really logging out, it's killing X, what happens when you do a regular logout?

---

### Post by NT4usB on 2007-08-14
iirc, the correct steps are:
If you want to log out, then simply log out.
If you want to restart X, log out first, then Ctrl+Alt+Backspace.
Don't know why it should matter.
I do know I get a lot less grief from my systems if I log out first.
ymmv...

---

### Post by chanman on 2007-08-15
either way I log out, by system -> quit -> logout or by killing X, it brings me back to the login window.

> **tribble222 said:**
> I'm not an expert, but maybe something is wrong with your gdm init file?  Does the command "sudo /etc/init.d/gdm restart" let you log in to gnome?  I'm not sure if you're seeing a login screen at all after you ctrl-alt-backspace.

I haven't touched my gdm init file.

here it is though:
```

#! /bin/sh
#
# Originally based on:
# Version:	@(#)skeleton  1.8  03-Mar-1998  miquels@cistron.nl
#
# Modified for gdm, Steve Haslam <steve@arise.dmeon.co.uk> 14mar99
# modified to remove --exec, as it does not work on upgrades. 18jan2000
# modified to use --name, to detect stale PID files 18mar2000
# sleep until gdm dies, then restart it 16jul2000
# get along with other display managers (Branden Robinson, Ryan Murray) 05sep2001

set -e

# To start gdm even if it is not the default display manager, change
# HEED_DEFAULT_DISPLAY_MANAGER to "false."
HEED_DEFAULT_DISPLAY_MANAGER=true
DEFAULT_DISPLAY_MANAGER_FILE=/etc/X11/default-display-manager
PATH=/sbin:/bin:/usr/sbin:/usr/bin
DAEMON=/usr/sbin/gdm
PIDFILE=/var/run/gdm.pid
UPGRADEFILE=/var/run/gdm.upgrade

if [ -e $UPGRADEFILE -a "$1" != "restart" -a "$1" != "force-reload" ]; then
	SSD_ARG="--startas $DAEMON"
	rm -f $UPGRADEFILE
else
	SSD_ARG="--exec $DAEMON"
fi

# Allow cdd to override the config
if [ -f /etc/gdm/gdm-cdd.conf ]; then
	CONFIG_FILE="--config=/etc/gdm/gdm-cdd.conf"
fi

test -x $DAEMON || exit 0

if [ -r /etc/environment ]; then
  if LANG=$(pam_getenv -l LANG); then
    export LANG
  fi
  if LANGUAGE=$(pam_getenv -l LANGUAGE); then
    export LANGUAGE
  fi

fi

. /lib/lsb/init-functions

case "$1" in
  start)
  	if [ -e "$DEFAULT_DISPLAY_MANAGER_FILE" -a "$HEED_DEFAULT_DISPLAY_MANAGER" = "true" -a "$(cat $DEFAULT_DISPLAY_MANAGER_FILE 2>/dev/null)" != "$DAEMON" ]; then
		log_warning_msg "Not starting GNOME Display Manager (gdm); it is not the default display manager."
	else
		log_begin_msg "Starting GNOME Display Manager..."
		# if usplash is running, make sure to stop it now, yes "start" kills it.
	        if pidof usplash > /dev/null; then
			usplash=:
			orig_console="$(fgconsole)"
			DO_NOT_SWITCH_VT=yes /etc/init.d/usplash start
			# We've just shut down usplash, so don't log
			# success as it will look weird on the console.
			log_end_msg=:
		else
			usplash=false
			log_end_msg=log_end_msg
		fi
		start-stop-daemon --start --quiet --oknodo --pidfile $PIDFILE --name gdm $SSD_ARG -- $CONFIG_FILE >/dev/null 2>&1 || log_end_msg 1
		$log_end_msg 0

		if $usplash && [ "$orig_console" != serial ]; then
			# Wait a short while for the active console to
			# change, to try to avoid visible console noise from
			# later init scripts.
			i=0
			while [ "$(fgconsole)" = "$orig_console" ]; do
				i="$(($i + 1))"
				if [ "$i" -gt 5 ]; then
					break
				fi
				sleep 1
			done
		fi
	fi
  ;;
  stop)
	log_begin_msg "Stopping GNOME Display Manager..."
	start-stop-daemon --stop  --quiet --oknodo --pidfile $PIDFILE --name gdm $SSD_ARG --retry 30 >/dev/null 2>&1
	log_end_msg 0
  ;;
  reload)
	log_begin_msg "Reloading GNOME Display Manager configuration..."
	log_warning_msg "Changes will take effect when all current X sessions have ended."
	start-stop-daemon --stop --signal USR1 --quiet --pidfile \
		$PIDFILE --name gdm $SSD_ARG >/dev/null 2>&1
	log_end_msg 0
  ;;
  restart|force-reload)
	$0 stop || true
	$0 start
  ;;
  *)
	log_success_msg "Usage: /etc/init.d/gdm {start|stop|restart|reload|force-reload}"
	exit 1
  ;;
esac

exit 0

```

---

