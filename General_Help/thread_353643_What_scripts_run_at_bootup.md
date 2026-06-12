---
title: "What scripts run at bootup?"
date: 2007-02-04
forum: General Help
---

### Post by rocketman768 on 2007-02-04
So, I need a little clarification on what scripts run at bootup. What about init.d and rc1.d and stuff? How does that all interact? I want to know because I would like to automate a few things, but I'm not sure if I stick a script in /etc/init.d that it will actually run. Thanks!

---

### Post by kerry_s on 2007-02-05
Put it in /etc/init.d/rc.local right under the #!/bin/sh. here's what mine looks like.->

```
#! /bin/sh

athcool on &
sudo -u user find /usr/lib/firefox ! -type d | xargs cat > /dev/null &
sudo -u user  find /home/user/.mozilla/firefox ! -type d | xargs cat > /dev/null &
hdparm -W1 -c3 -m16 /dev/hda &


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

```

---

### Post by feld on 2007-02-05
LOL!

You're supposed to put those lines in /etc/rc.local, not in the INITSCRIPT! :D

---

### Post by kerry_s on 2007-02-05
> **feld said:**
> LOL!

You're supposed to put those lines in /etc/rc.local, not in the INITSCRIPT! :D

I did not even know there was one there. :confused:
Well it works in both places. :)
But i moved mine there and will start using that location, it's less likely to screw up things since that one is empty by default.

```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

athcool on &
sudo -u user find /usr/lib/firefox ! -type d | xargs cat > /dev/null &
sudo -u user  find /home/user/.mozilla/firefox ! -type d | xargs cat > /dev/null &
hdparm -W1 -c3 -m16 /dev/hda &


exit 0

```

---

### Post by rocketman768 on 2007-02-05
Haha, thanks guys. Anything else I should know?

---

### Post by kerry_s on 2007-02-05
> **rocketman768 said:**
> Haha, thanks guys. Anything else I should know?

Make sure you use your startup scripts? :) 

athcool on &  <starts athcool, keeps my athlon processor in the 27c-40c
sudo -u user find /usr/lib/firefox ! -type d | xargs cat > /dev/null &  <-preloads firefox
sudo -u user  find /home/user/.mozilla/firefox ! -type d | xargs cat > /dev/null &  <preloads firefox
hdparm -W1 -c3 -m16 /dev/hda &  <- speeds up my hda drive


You can use the "preload firefox" ones safely, but you need to change "user" to what ever your name is, "user" is the name i use for my test account and to mess around, its what i use to login most of the time. :)

---

### Post by aktiwers on 2007-02-05
Would that :
athcool on &  <starts athcool, keeps my athlon processor in the 27c-40c

work on my AMD athlon XP 2800+ ?
And would it slow it down?

---

### Post by kerry_s on 2007-02-05
> **aktiwers said:**
> Would that :
athcool on &  <starts athcool, keeps my athlon processor in the 27c-40c

work on my AMD athlon XP 2800+ ?
And would it slow it down?

Yep, it would work, but you need to install it first. 
 sudo apt-get install athcool <- it's in the universe repo, so you need to have all your repos turned on.
No it does not slow it down.

---

### Post by aktiwers on 2007-02-05
Thanks just installed and added it.. :D
Gonna reboot..

---

### Post by kerry_s on 2007-02-05
You might also want to try conky, to keep a eye on all that fun info->

---

### Post by jimbob on 2007-02-05
Why doesn't conky show any swap ??
________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="2"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

### Post by kerry_s on 2007-02-05
> **jimbob said:**
> Why doesn't conky show any swap ??
________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="2"]*Registered Linux User #400396*[/SIZE][/COLOR]

I deleted my swap space, it never ever has been used, i have 1 gig of ram. With no apps open my ram is only 9% used. It has never even made it to 50% even with me multi tasking on dual monitors and 4 virtual desks. :confused:

Here's a pic, i have a firefox on each virtual desk with 6 tabs open in each, i have thunar on the other side of each desk and i have 1 firefox playing pandora music, and my ram barely moves.

My system has always been good on resources. :)
I guess i just don't do enough.

---

### Post by jimbob on 2007-02-05
Don't know that much about it but when I was running Vmware with XP as a virtual machine under Ubuntu my system was swapping quite a bit.  I also have 1GB of memory.
________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="2"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

