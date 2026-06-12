---
title: "my script won't run on startup"
date: 2016-01-20
forum: General Help
---

### Post by wilk3sy on 2016-01-20
Linux really isn't my friend today. 

So I read this 

[http://askubuntu.com/questions/228304/how-do-i-run-a-script-at-start-up](http://askubuntu.com/questions/228304/how-do-i-run-a-script-at-start-up)

made my script 

> #! /bin/bash
#

case "$1" in
	start)
	ids=$(xinput --list | awk -v search="3M" \
		'$0 ~ search {match($0, /id=[0-9]+/);\
		if (RSTART) \
		print substr($0, RSTART+3, RLENGTH-3)\
		}'\
		)
	ar=($ids)
		xinput map-to-output ${ar[0]} HDMI3 
		xinput map-to-output ${ar[1]} HDMI1 
		xinput map-to-output ${ar[2]} HDMI2 
	;;

esac

exit 0

Can anyone see anything obviously wrong with that?

---

### Post by pfeiffep on 2016-01-20
My first thought - did you make the script (file) executable

---

### Post by wilk3sy on 2016-01-20
Yeah I followed the first method on that post I linked above. 

I know the script works as when I run it after startup, it configures the touchscreens. With this in mind, I decided to use the upstart method of putting a .conf file into /etc/init, but this had the same results. 

my only thoughts at this point, is it's working as expected, but the screens locations are being configured AFTER the touchscreen controls. My theory behind this is that all three monitors show the same thing initially AND then they get configured in the order required. However I don't know if linux is doing this automatically OR if there is another script running somewhere that someone prior to me getting this computer has put in place.

---

### Post by ian-weisser on 2016-01-20
That AskUbuntu question is three years old. Changes have happened.
That's a sysvinit script, so you're using runlevels. Those go in /etc/init.d, and require an LSB header and runlevel selections.

Upstart (in Ubuntu 12.04 and 14.04) has sysvinit compatibility, but it's imperfect. Upstart doesn't use runlevels. You might do better creating a specific Upstart job in /etc/init. Perhaps one of our 14.04 users can suggest an existing Upstart job or signal to use as a dependency for yours.

systemd (in UBuntu 15.10 and 16.04 and newer) has sysvinit compatibility, but it's imperfect. systemd doesn't use  runlevels. You might do better creating a specific systemd task in  /etc/init. Perhaps one of our 16.04 users can suggest an existing systemd target to use.

Which release of Ubuntu are you running?

---

### Post by wilk3sy on 2016-01-20
Thanks. 

I'm running 14.04

I was able to run the script after logon using Startup Applications, but this isn't how I'd like to leave it.

---

