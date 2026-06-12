---
title: "Problem using notify-send as root"
date: 2008-04-29
forum: General Help
---

### Post by ashikahamed on 2008-04-29
When I use notify-send in scripts run by using '/etc/crontab' notifications are not displayed in Hardy.
In gusty doing the following
```
DBUS_SESSION_BUS_ADDRESS="dbus session address of the user" sudo -u "user" notify-send "Some text"
```
displays notifications but when I use this in Hardy I get the following error
```
libnotify-Message: Unable to get session bus: Failed to connect to socket /tmp/dbus-'some random text': Connection refused
```

Is there any other way to make scripts executed by '/etc/crontab' to display notifications in Hardy?

---

### Post by Chief677 on 2008-11-02
Hey,

I know this is an old question but I worked out a solution right now and maybe you still need a soulution :-)

I'm running a sync script hourly with cron and want to be notified via libnotify, so I had the same problem as you had :-) Here is my code piece which does the notification for me:

```

#!/bin/sh

init_notify() {
	user=`whoami`
	pids=`pgrep -u $user nautilus`
	for pid in $pids; do
		# find DBUS session bus for this session
		DBUS_SESSION_BUS_ADDRESS=`grep -z DBUS_SESSION_BUS_ADDRESS /proc/$pid/environ | sed -e 's/DBUS_SESSION_BUS_ADDRESS=//'`
		# use it
		export DBUS_SESSION_BUS_ADDRESS=$DBUS_SESSION_BUS_ADDRESS
	done
}

notify() {
	if [ -z "$DBUS_SESSION_BUS_ADDRESS" ]; then
		init_notify
	fi
	
	title=$1
	text=$2
	timeout=$3
	
	if [ -z "$title" ]; then
		return
	fi
	if [ -z "$text" ]; then
		text=$title
	fi
	if [ -z "$timeout" ]; then
		timeout=5000
	fi
	
	notify-send "$title" "$text" -t $timeout
}

```

Just copy&paste these two funtions into your script and just type 'notify "title" "text" 5000' in your script where you want to send a notification.
Don't forget to write the correct username in the "init_notification()" function.

c,Ya

---

### Post by outleradam on 2009-12-27
what about if another user calls the script.  I have a second user calling scripts on my computer which requires me to get a notification when the script is called.  

How do I set it up so that script notifies my main desktop?

---

