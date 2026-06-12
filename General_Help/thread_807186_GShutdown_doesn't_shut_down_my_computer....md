---
title: "GShutdown doesn't shut down my computer..."
date: 2008-05-25
forum: General Help
---

### Post by MORDOCtheGREAT on 2008-05-25
I installed GShutdown through Applications>add/remove and when I use it, it just logs the user out without shutting the computer down.

---

### Post by Warmask on 2008-05-25
I use "Alarm Clock" to schedule shutdowns, and I learned that I need to run a command before the program would properly shutdown.

su chmod u+s /sbin/shutdown

after that, the program shutsdown fine for me. I use the command "shutdown -P now"
Hope that helps.

---

### Post by Big Wig !!! on 2008-07-26
Get this file [http://sat2000.sourceforge.net/](http://sat2000.sourceforge.net/) :KS

---

### Post by angry_johnnie on 2008-07-26
Here's a script I wrote for a friend who was having a similar problem.

Code's kinda dirty, but it works alright. :-)

```
#!/bin/bash

### Powerthing by A.J.
###
### Send me money!
### Alright... don't send me money...
###

if ! $(zenity --question --no-wrap --title "Power Thingie" --text "This script will shutdown/reboot your computer.
\n Continue?") ; then
	exit 0
fi

PASSWORD=$(zenity --title='Password' --text='Enter your password' --entry --hide-text)
if $PASSWORD
	then
	exit 0
fi

PARAMETER=$(zenity --list --title "Parameters" --text "Choose action"\
		--radiolist \
		--column "Pick" --column "Value" --column "Meaning" \
		ONE	r	"Reboot" \
		TWO	h	"Shutdown" \
		THREE	c	"Cancel Previous"
)
if $PARAMETER
	then
	exit 0
fi
if [ "${PARAMETER}" == "c" ]; then
echo $PASSWORD | sudo shutdown -$PARAMETER now
zenity --info --title='Done' --text='The previous shutdown process has ben terminated.'
	exit 0
fi

REPLY=$(zenity --scale --title="Delay" --text "Choose delay time. (minutes)" --min-value=1 --max-value=240 --value=1 --step 1)
if $REPLY
	then
	exit 0
fi

if ! $(zenity --question --no-wrap --title "Power Thingie" --text "Are you sure you want to do this?") ; then
	exit 0
fi

gnome-screensaver-command --activate --lock

echo $PASSWORD | sudo shutdown -$PARAMETER $REPLY
```

---

### Post by monjope on 2008-08-15
The script works great. Thanks.

---

### Post by imwithid on 2009-10-20
> **Big Wig !!! said:**
> Get this file [http://sat2000.sourceforge.net/](http://sat2000.sourceforge.net/) :KS

This program does not work in 9.10 Karmic (Beta - Daily Build Oct. 19-2). In the terminal window, it stops at asking for the password.

---

### Post by imwithid on 2009-10-20
> **angry_johnnie said:**
> Here's a script I wrote for a friend who was having a similar problem.

Code's kinda dirty, but it works alright. :-)

```
#!/bin/bash

### Powerthing by A.J.
###
### Send me money!
### Alright... don't send me money...
###

if ! $(zenity --question --no-wrap --title "Power Thingie" --text "This script will shutdown/reboot your computer.
\n Continue?") ; then
	exit 0
fi

PASSWORD=$(zenity --title='Password' --text='Enter your password' --entry --hide-text)
if $PASSWORD
	then
	exit 0
fi

PARAMETER=$(zenity --list --title "Parameters" --text "Choose action"\
		--radiolist \
		--column "Pick" --column "Value" --column "Meaning" \
		ONE	r	"Reboot" \
		TWO	h	"Shutdown" \
		THREE	c	"Cancel Previous"
)
if $PARAMETER
	then
	exit 0
fi
if [ "${PARAMETER}" == "c" ]; then
echo $PASSWORD | sudo shutdown -$PARAMETER now
zenity --info --title='Done' --text='The previous shutdown process has ben terminated.'
	exit 0
fi

REPLY=$(zenity --scale --title="Delay" --text "Choose delay time. (minutes)" --min-value=1 --max-value=240 --value=1 --step 1)
if $REPLY
	then
	exit 0
fi

if ! $(zenity --question --no-wrap --title "Power Thingie" --text "Are you sure you want to do this?") ; then
	exit 0
fi

gnome-screensaver-command --activate --lock

echo $PASSWORD | sudo shutdown -$PARAMETER $REPLY
```



Sorry to say that this one doesn't work  on Karmic, either. The screen goes blank as soon as I select the last prompt. Anyone else have any suggestions?

---

### Post by imwithid on 2009-10-20
> **Warmask said:**
> I use "Alarm Clock" to schedule shutdowns, and I learned that I need to run a command before the program would properly shutdown.

su chmod u+s /sbin/shutdown

after that, the program shutsdown fine for me. I use the command "shutdown -P now"
Hope that helps.

No dice here either. There doesn't seem to be anything out there for Karmic for automatically shutting down one's computer.

---

### Post by realzippy on 2009-11-02
Dirty solution for me is to give shutdown superuser flag:

**sudo chmod +s /sbin/shutdown**

On a multi user system this might cause trouble of course  ;-),
but on a single user system this is a solution to make gshutdown work..

---

### Post by centos on 2009-11-04
> **realzippy said:**
> 
**sudo chmod +s /sbin/shutdown**

Doesn't work for me neither. GShutdown stopped working just after updating to Karmic. I also end up with login screen, sometimes it even wakes me up at night because for some reason CPU is doing something (some error, probably..) and my laptop is not really quiet.

I tried SAT2000 mentioned here but only empty window opens.
Of course i could write a single script (as I had before) for shutting down after 30 minutes or whatever, but GShutdown is nice for ability to set that up with mouse only.

---

### Post by realzippy on 2009-11-08
Try editing the shutdown command in gshutdown.
After sudo chmod +s /sbin/shutdown open gshutdown properties,choose own command for shutdown:

**shutdown -h now**

---

### Post by centos on 2009-11-09
I will test it this night, thanks for a hint.

edit: it's working, great.

---

### Post by algonco on 2009-11-16
Not work for me.
gnome still show me this warning: "Warning! : your computer is going to shutdown now! "
To options: cancel or execute.
Only if i choose execute th computer is shutdown.

Any ideas?

Thanks.

---

### Post by realzippy on 2009-11-16
you have run:

sudo chmod +s /sbin/shutdown   ??

---

### Post by algonco on 2009-11-18
Sorry, it works great.

Thanks:)

---

### Post by angry_johnnie on 2009-11-26
ok this one does work on karmic.  i've tested it.  ;)

---

### Post by hnavag73 on 2011-02-09
> **realzippy said:**
> Try editing the shutdown command in gshutdown.
After sudo chmod +s /sbin/shutdown open gshutdown properties,choose own command for shutdown:

**shutdown -h now**

works great, thanks!

---

### Post by daftlad on 2011-02-10
I could never shut down my computer with Gshutdown, found Qshutdown to be the only one that works for me....

---

