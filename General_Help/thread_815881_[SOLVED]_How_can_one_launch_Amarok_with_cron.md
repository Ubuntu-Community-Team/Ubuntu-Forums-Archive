---
title: "[SOLVED] How can one launch Amarok with cron?"
date: 2008-06-02
forum: General Help
---

### Post by descentspb on 2008-06-02
It just doesn't work. With "at" also. Tried to launch "gnome-terminal -e 'amarok -p'" from cron and it even can't launch gnome-terminal itself from cron or at. Thanks in advance

---

### Post by RAOF on 2008-06-02
Why are you trying to launch Amarok from cron?  Is this some sort of poor-man's alarm clock? :).

At least one problem is going to be that cron doesn't have any of the environment variables X apps assume will be set.  You might be able to get things partially working by setting the DISPLAY variable - launching gnome-terminal with
```
DISPLAY=:0 gnome-terminal -e 'amarok -p'
```
but that may only result in gnome-terminal or amarok complaining about some other piece of expected environment.

---

### Post by descentspb on 2008-06-02
Well, yes, it is for alarm clock ) But i wouldn't say it's poor. Cause i have amarok launched with a configured playlist, and what is needed for an alarm is just "the play button to be pushed". With play, or mplayer or anything else, it wouldn't be as convinient to manage the song list for your morning. And thanks for the advice, i'll try that when i can.

---

### Post by descentspb on 2008-06-02
it's a pitty, but it's not working, exactly as you predicted. It launches the terminal though

---

### Post by descentspb on 2008-06-02
Figured out the way to do it. Just "DISPLAY=:0 amarok -p" does the job. Thanks.

---

### Post by pirithiumx on 2008-08-26
Awsome Thx. :guitar: 
I spent Much Time Trying to Figure this one Out but now after seeing your post, Wahlaa!! Its so obvious, the cron Task had no Idea where amarok was. hence would not run.
I am sure this is somthing to watch out for on other applications as well. 
I use amarok & Cron for a break bell system for a manufacturing plant. 
The alsa player I was using keeps crashing so I tried using amarok instead. Except it would not work when run from cron. 


bell.sh with parameter

#!/bin/sh
#
if [ -n "$1" ]
then
	if [ "$1" = 1 ]
	then
	DISPLAY=:0 amarok -l /root/breakbell/Sounds/FirstOne.ogg 
       DISPLAY=:0 amarok -p
	fi
	if [ "$1" = 2 ]
	then 
	DISPLAY=:0 amarok -l /root/breakbell/Sounds/FirstTwo.ogg
	DISPLAY=:0 amarok -p
	fi	
	if [ "$1" = 3 ]
	then 
	DISPLAY=:0 amarok -l /root/breakbell/Sounds/FirstThree.ogg 
	DISPLAY=:0 amarok -p
	fi
fi

I use three diferent sound files of the bells which are like C chord chimes. When I tried playing a single file three times - back with ALSA Player I would get misplays somtimes. Or one would cut out. etc. So I broke it up into three seperate audio files.  
I like to Run the Play Command after it loads, sometimes the file would play short. Or it did when I was using the ALSAPLayer.

crontab example:

00 7 * * * /root/breakbell/bell.sh 2
00 9 * * * /root/breakbell/bell.sh 2
13 9 * * * /root/breakbell/bell.sh 1
15 9 * * * /root/breakbell/bell.sh 2
55 9 * * * /root/breakbell/bell.sh 2
08 10 * * * /root/breakbell/bell.sh 1
10 10 * * * /root/breakbell/bell.sh 2
10 12 * * * /root/breakbell/bell.sh 2

Note I placed a script in KDE autostart to start Amarok when the System Boots. Since the machine this runs on only does remote backupos and break buzzers.
This system works well and I have been using it for over 2 years now.

---

### Post by pcozzy on 2008-10-19
great info 
thanks,
:guitar:

---

