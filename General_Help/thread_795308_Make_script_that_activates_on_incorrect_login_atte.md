---
title: "Make script that activates on incorrect login attempt?"
date: 2008-05-15
forum: General Help
---

### Post by igor.d on 2008-05-15
What I want to achieve is to do some action when I or some other user of my PC/laptop enters incorrect password/username at the login screen.

I have made success doing this for closing and opening of my laptop lid to play a certain sound :) Now I want to achieve this on the login incorrect attempt.

I do know how to make and activate scripts on logging in but I am highly interested in doing this!!! Please - Ubuntu community - help this guy ;)

Thanks!!

---

### Post by cdenley on 2008-05-15
I don't think this is possible if you're logging in or authenticating from the terminal, but if you want to play a sound when a login fails in GDM...

System>Administration>Login Window
select the "Accessibility" tab

---

### Post by bingoUV on 2008-05-15
All failed login attempts are stored in a log file. In my system (fedora) they go in /var/log/secure. Check yours. Otherwise it might be /var/log/messages. One way to check is run the following just after a failed login attempt
```

sudo ls -ltr /var/log/

```
In the output of the above, the last few files are of your interest.

Run a cron job that monitors this file. This file is likely to be readable only by root, so run the cron tab from root's account.

If you are upto C programming, you could write up a small program using inotify to tell you when this file is changed and then take appropriate action. No need for cron in that case.
```

man inotify

```

EDIT : 
Seems like you don't need C programming. Install inotify-tools from repositories and you should get what you want. Not tried so cannot help you further, but it should be very useful.

---

### Post by igor.d on 2008-05-15
[SOLVED]

Ok, I am definitely noob :), just forgot about looking into System settings!
Thank you both!!!

---

### Post by pwnfactory on 2008-07-05
Could you please post how you solved this, thanks. I'm trying to use the built-in webcam take a picture on incorrect login event.

---

### Post by l0fls on 2008-07-05
> **igor.d said:**
> What I want to achieve is to do some action when I or some other user of my PC/laptop enters incorrect password/username at the login screen.

I have made success doing this for closing and opening of my laptop lid to play a certain sound :) Now I want to achieve this on the login incorrect attempt.

I do know how to make and activate scripts on logging in but I am highly interested in doing this!!! Please - Ubuntu community - help this guy ;)

Thanks!!

can you pm me hoe you did the sound when laptop lid opens/closes

---

### Post by igor.d on 2008-07-05
> **l0fls said:**
> can you pm me hoe you did the sound when laptop lid opens/closes

Hi, laptop LID is a button just like any other laptop button whose state is being detected in /proc/acpi/button/lid... Now, the scripts which control the actions are inside /etc/acpi... Here is how my **/etc/acpi/lid.sh** looks like :)
I'm using mpg123 to play some mp3 music. Easy :)

```

#!/bin/bash

if [ ! "$(cat /proc/acpi/button/lid/LID/state | grep closed)" = "" ]; then
mpg123 "/home/dave/Documents/Chimes/camera.mp3"
fi

if [ ! "$(cat /proc/acpi/button/lid/LID/state | grep open)" = "" ]; then
mpg123 "/home/dave/Documents/Chimes/sword.mp3"
fi

. /usr/share/acpi-support/power-funcs
. /usr/share/acpi-support/policy-funcs
. /etc/default/acpi-support

[ -x /etc/acpi/local/lid.sh.pre ] && /etc/acpi/local/lid.sh.pre

if [ `CheckPolicy` == 0 ]; then exit; fi

grep -q closed /proc/acpi/button/lid/*/state
if [ $? = 0 ]
then
    mpg123 /home/dave/Documents/Chimes/sony.mp3
    for x in /tmp/.X11-unix/*; do
	displaynum=`echo $x | sed s#/tmp/.X11-unix/X##`
	getXuser;
	if [ x"$XAUTHORITY" != x"" ]; then
	    export DISPLAY=":$displaynum"	    
	    . /usr/share/acpi-support/screenblank
	fi
     done
else
    for x in /tmp/.X11-unix/*; do
	displaynum=`echo $x | sed s#/tmp/.X11-unix/X##`
	getXuser;
	if [ x"$XAUTHORITY" != x"" ]; then
	    export DISPLAY=":$displaynum"
	    grep -q off-line /proc/acpi/ac_adapter/*/state
	    if [ $? = 1 ]
		then
		if pidof xscreensaver > /dev/null; then 
		    su $user -c "xscreensaver-command -unthrottle"
		fi
	    fi
	    if [ x$RADEON_LIGHT = xtrue ]; then
		[ -x /usr/sbin/radeontool ] && radeontool light on
	    fi
	    if [ `pidof xscreensaver` ]; then
		su $user -c "xscreensaver-command -deactivate"
	    fi
	    su $user -c "xset dpms force on"
	fi
    done
fi
[ -x /etc/acpi/local/lid.sh.post ] && /etc/acpi/local/lid.sh.post

```

---

