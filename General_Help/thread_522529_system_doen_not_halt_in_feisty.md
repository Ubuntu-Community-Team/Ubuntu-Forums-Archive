---
title: "system doen not halt in feisty"
date: 2007-08-10
forum: General Help
---

### Post by true_friend on 2007-08-10
Hi folks
have a little problem. Using Ubuntu converted to kubuntu, not upgraded to latest packages i mean latest kernal 2.6.20 etc. Problem is i cannot shutdown the system. It conveys a message at the end of system halt, then after a few seconds a message comes system is halted but power is not turned off.
Any idea?
Regards
True_Friend

---

### Post by moore.bryan on 2007-08-10
*try checking to make sure your /etc/default/halt file has the default behavior as poweroff.*

---

### Post by true_friend on 2007-08-10
This is the out put of this file and I think it is as you said.
> # Default behaviour of shutdown -h / halt. Set to "halt" or "poweroff".
HALT=poweroff
seems some kernal problem?

---

### Post by moore.bryan on 2007-08-10
*i had a very similar problem, but my laptop kept rebooting when i wanted it to poweroff.... turned out i had a reboot symlink in my /etc/rc0.d directory; deleting it fixed the issue.  which files are in your /etc/rc0.d folder?*

---

### Post by true_friend on 2007-08-11
hmmm
I think this S90halt.sh in this folder may be of our interest. 
The contents are
> #! /bin/sh
### BEGIN INIT INFO
# Provides:          halt
# Required-Start:    umountroot
# Required-Stop:
# Should-Start:      lvm raid2
# Should-Stop:
# Default-Start:     0
# Default-Stop:
# Short-Description: Execute the halt command.
# Description:
### END INIT INFO

PATH=/usr/sbin:/usr/bin:/sbin:/bin
[ -f /etc/default/halt ] && . /etc/default/halt

. /lib/lsb/init-functions

do_stop () {
	if [ "$INIT_HALT" = "" ]
	then
		case "$HALT" in
		  [Pp]*)
			INIT_HALT=POWEROFF
			;;
		  [Hh]*)
			INIT_HALT=HALT
			;;
		  *)
			INIT_HALT=POWEROFF
			;;
		esac
	fi

	# See if we need to cut the power.
	if [ "$INIT_HALT" = "POWEROFF" ] && [ -x /etc/init.d/ups-monitor ]
	then
		/etc/init.d/ups-monitor poweroff
	fi

	# Don't shut down drives if we're using RAID.
	hddown="-h"
	if grep -qs '^md.*active' /proc/mdstat
	then
		hddown=""
	fi

	# If INIT_HALT=HALT don't poweroff.
	poweroff="-p"
	if [ "$INIT_HALT" = "HALT" ]
	then
		poweroff=""
	fi

	log_action_msg "Will now halt"
	sleep 1
	halt -d -f -i $poweroff $hddown
}

case "$1" in
  start)
	# No-op
	;;
  restart|reload|force-reload)
	echo "Error: argument '$1' not supported" >&2
	exit 3
	;;
  stop)
	do_stop
	;;
  *)
	echo "Usage: $0 start|stop" >&2
	exit 3
	;;
esac

:


---

### Post by moore.bryan on 2007-08-11
*same as mine, so i don't think it's that file.  what are the other files in /etc/rc0.d?*

---

### Post by true_friend on 2007-08-12
Other files by name are as follows:
K01gdm, K01kdm, K01usplash, K19hplip, K20apport, K25hwclock.sh, K50alsa-utils, S01linux-restricted-modules-common, S15wpa-ifupdown, S20sendsigs, S30urandom, S31umountnfs.sh, S40umountfs, S60umountroot, S90halt...
Pasting their contents would let the message too long. So any suspicious thing you can find from here?
Regards

---

### Post by moore.bryan on 2007-08-13
*how about this: try typing ```
sudo shutdown -hP now
``` in the terminal and post results... *

---

### Post by true_friend on 2007-08-17
Shut downs the sys.
no power off as usual and no out put obviously....

---

### Post by moore.bryan on 2007-08-17
[I]okay, someone else in another thread has the same issue... he is also, as you are, missing a link in your rc0.d to kill the rc.local script.  i suggested he make one, but he hasn't posted yet if it worked... you're free to try it, too...
```
sudo ln -s /etc/rc0.d/K01rc.local /etc/init.d/rc.local
```
[/I]

---

### Post by true_friend on 2007-08-17
ok i post its result.
thnx

---

### Post by moore.bryan on 2007-08-17
*it didn't work for him, so it'll be REALLY strange if it works for you.*

---

### Post by true_friend on 2007-08-18
yup it is just normal here also. didnt worked here also. the output:::::
> ss@ss-desktop:~$ sudo ln -s /etc/rc0.d/K01rc.local /etc/init.d/rc.local
Password:
ln: creating symbolic link `/etc/init.d/rc.local' to `/etc/rc0.d/K01rc.local': File exists
ss@ss-desktop:~$
File exists mean no way.....

---

### Post by moore.bryan on 2007-08-19
*that's weird because in one of the posts above, you didn't include it in the list... go into the /etc/rc0.d dir and make sure K01rc.local is there...*

---

### Post by true_friend on 2007-08-22
no this is not there.
so what to do?
that command is saying all is ok.

---

### Post by moore.bryan on 2007-08-24
*is there a file named K01rc.local in /etc/rc0.d?*

---

### Post by true_friend on 2007-08-24
No there is not such file.

---

### Post by moore.bryan on 2007-08-24
*okay... double-check to make sure there's a file named "rc.local" in /etc/init.d.*

---

### Post by true_friend on 2007-08-24
This file is there with the same name in "/etc/init.d". The contents are as follows 
-------------------------------------------------------------------------------------------
#! /bin/sh

PATH=/sbin:/bin:/usr/sbin:/usr/bin
[ -f /etc/default/rcS ] && . /etc/default/rcS
. /lib/lsb/init-functions

do_start() {
	if [ -x /etc/rc.local ]; then
		log_begin_msg "Running local boot scripts (/etc/rc.local)"
		/etc/rc.local
		log_end_msg $?
	fi
}

case "$1" in
    start)
	do_start
        ;;
    restart|reload|force-reload)
        echo "Error: argument '$1' not supported" >&2
        exit 3
        ;;
    stop)
        ;;
    *)
        echo "Usage: $0 start|stop" >&2
        exit 3
        ;;
esac
---------------------------------------------------------------------------------------
Regards

---

### Post by moore.bryan on 2007-08-25
[I]so, once again, try putting a symlink file in /etc/rc0.d that aims at the /etc/init.d/rc.local script:
```
[/I]sudo ln -s /etc/init.d/rc.local /etc/rc0.d/K01rc.local[I]
```
now, you shouldn't get a message saying there's a file there because you've already checked and there isn't...
[/I]

---

### Post by true_friend on 2007-08-26
made a symbolic link but nothing changed.
Regards

---

### Post by moore.bryan on 2007-08-26
*okay, try this... hit ctrl, alt, and backspace all at the same time.  when the xserver quits and you have the command prompt, type ```
sudo poweroff now
``` did it poweroff for you?*

---

### Post by Romanus81 on 2007-08-26
I'm having the same problem. I started looking the halt script in the rc0.d folder, and found
> 
log_action_msg "Will now halt"
sleep 1
halt -d -f -i $poweroff $hddown
}
for the sake of messing with my system I typed in "sudo halt", then my password, and my computer stopped, it didn't give me the progress bar except for the last few seconds, and then it shutdown. The disk was turned off, but I'm still a new to linux and not sure if this is the healthiest option.
I've gone through two installs of ubuntu, one was using Wubi (used virtual disks in windows instead of a partition), the second was on a real partition installed with the liveCD. Both had the same problem.

---

### Post by fjgaude on 2007-08-26
I trust all here are using the latest BIOS updates to their motherboards... all this not halting stuff sounds like an MB issue, not a Ubuntu one.

frank

---

### Post by TrevorNC on 2007-08-27
Check here for how I solved this problem [http://ubuntuforums.org/showthread.php?p=3264016#post3264016]("http://ubuntuforums.org/showthread.php?p=3264016#post3264016")

---

### Post by true_friend on 2007-08-28
TrevorNC: Tanks a lot
your solution worked for me as well. Added that code at end of both lines (Noraml + Recovery Mode). After restarting when I turned off the computer it shut down and power also off.
Thnx once again.
Regards

---

