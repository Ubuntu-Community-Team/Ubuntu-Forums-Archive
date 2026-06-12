---
title: "Whats wrong with my /etc/rc.local file ?"
date: 2008-06-05
forum: General Help
---

### Post by hal8000 on 2008-06-05
Need a little help, running Ubuntu 8.04, booting to runlevel 2 without problems.
I have modified /etc/rc.local to include a script to enable numlock but its failing to work.
Heres my /etc/rc.local:

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
echo -e "\E[33m Enabling Number Lock"
/usr/bin/numlockx &
sleep 2
exit 0


In my script I have attempted to colorize the output with the echo command, the sleep 2 is to create added delay.
If I type:
/etc/init.d/rc.local start

this runs my script and enables number lock.
If I type /etc/rc.conf this also works and enables number lock.

However if I reboot then the script is either ignored but number lock is not enabled??

I've loaded bootchart and can even see the S99rc.local script and final sleep command, so why is this failing?
Bootchart attached.

P.S. Pressing alt-F1 and disabling splash screen, I see all the console messages, final boot message about numlock is too quick to read and it ignores sleep 2 in rc.local

Thanks in advance.

---

### Post by drs305 on 2008-06-05
I'll take a look at your entry but a much easier way to set up numlock is the following, which saves the last state:

```
gconftool-2 --type bool --set /desktop/gnome/peripherals/keyboard/remember_numlock_state "true"
 
```

---

### Post by ibuclaw on 2008-06-05
Try:
```
/usr/bin/numlockx on &
```

[EDIT]
I've just tried it in a virtual terminal and I get an error like this:
> 
Error Opening Display!

Maybe that's why it won't work...

To be sure, change the command to this:
```
/usr/bin/numlockx && echo "SUCCESS" > /home/<yourname>/numlockx.log || echo "FAILED" >/home/<yourname>/numlockx.log
```
Replacing <yourname> with your username.
Then check the newly created log file for whether or not the command ran successfully.

Regards
Iain

---

### Post by drs305 on 2008-06-05
> **tinivole said:**
> Try:
```
/usr/bin/numlockx on &
```

[EDIT]
I've just tried it in a virtual terminal and I get an error like this:

Maybe that's why it won't work...

Regards
Iain


Normally you have to add this "export DISPLAY=:0 &&" before gui commands but I didn't think numlockx would require it. It might solve things.

---

### Post by sdennie on 2008-06-05
If numlockx is a X an program, /etc/rc.local is probably not an appropriate place to run it.  Is there a reason you can't put it in your session login?  System->Preferences->Session.

---

### Post by ibuclaw on 2008-06-05
+1 to vor :)

Found a howto...
[https://help.ubuntu.com/community/NumLock](https://help.ubuntu.com/community/NumLock)

Regards
Iain

---

