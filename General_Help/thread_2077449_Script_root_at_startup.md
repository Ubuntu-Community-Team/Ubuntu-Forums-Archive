---
title: "Script root at startup"
date: 2012-10-28
forum: General Help
---

### Post by zooobie on 2012-10-28
Hi.

I wrote a script in order to shutdown my computer while I am watching a movie. If I am sleeping, the script has to shutdown my computer or else I have to press a key to prove that I am still awake.

I would like to run this script automatically at startup.
This script has to be run as root (the owner is the root) (since there are some commands like kill or shutdown). 
It may have been several solutions:
I would like to avoid to change the fact that commands such as "kill" or "shutdown" can be run by a non-administrator user (cf viduso) : my script has to be launch by the root user but I don't want to tape my passwword at startup.

I saw that a solution consists in make/change a startup script such as /etc/local.rc (I tried putting "xterm -e my_script.sh" at the but nothing is changed at the startup.
I have to run this script in a terminal (since I have to interact with this script a few minutes after the startup).

I just give you the source code:

```
#!/bin/bash
#shut your computer while watching a movie with Mplayer or Vlc
#version 10/1012

if test `id -u` != "0"; then
	echo "You are not the BigBoss"
	exit 1
fi

if [ $# -eq 0 ];
then 
	LIMIT=20
else
	LIMIT="$1"
fi

echo "########################################################################"
echo "# ZOOBIE's gonna shutdown itself in $LIMIT "
echo "minutes (subject to vlc or mp) #"
echo "########################################################################"

ENDORMI=0

while [ "$ENDORMI" -eq 0 ]
do

	sleep "$LIMIT"m

	PID=`ps -e | grep "mplayer\|vlc" | awk '{print $1}'`

	if [ ! -z "$PID" ]
	then
		sudo kill -STOP "$PID" 
		#kill -STOP "$PID" 
		APP=`wmctrl -l | grep "Terminal" | awk '{print $1}'`
		wmctrl -i -a "$APP"
	fi

	echo "Are you sleeping ?"
	read -n1 -t 17 ENDORMI	

	if [ ! -z "$ENDORMI" ]
	then
		ENDORMI=0
		if [ ! -z "$PID" ]
		then
			APP=`wmctrl -l | grep "MPlayer\|VLC" | awk '{print $1}'`
			wmctrl -i -a "$APP"
			kill -CONT "$PID"
			echo "Keep watching"
			continue
		fi
	else
		ENDORMI=1
	fi

done

shutdown -P now

echo "				SLEEP     TIGHT"
exit(0)
```


Any suggestions ?

---

### Post by JKyleOKC on 2012-10-28
You were on the right track, but there's no need to use xterm to run your script from rc.local. Just invoke the script, on a line just before the existing "exit 0" line.

Note that this will run during the boot sequence, long before anyone has logged in. It runs in a console, but it's one that has no keyboard or monitor attached, so all instructions have to be coded into the script or passed on the command line in rc.local. You won't be able to interact with the script at that point, and possibly never. All file and command references, also, have to be absolute paths, not relative, since the PATH environment variable is not yet set up and in any event is different for root and normal users. And your messages won't go anywhere; they'll just waste a few cycles of CPU time.

If you run it automatically at startup, it will shut down your machine after 20 minutes unless you tell it you're awake, no matter whether you're watching a movie or trying to read your e-mail. Perhaps a desktop launcher icon would be a less irritating way to start it, and would allow your messages and interaction -- but it's your system so you can set it up any way you want!

EDIT: Incidentally, you can edit the /etc/sudoers file, using visudo, to allow just your script, nothing else, to run via sudo without requiring a password. That would let you launch from an icon without having to input the password.

---

