---
title: "Kubuntu Power Button brings up shut down menu instead of proceding to shutdown"
date: 2007-12-25
forum: General Help
---

### Post by SergeiFranco on 2007-12-25
Here is the problem:
I have completely 3 different systems with Kubuntu 7.10 installed, the systems are: VIA EPIA-N C7 (with acpi=force), Athlon/nForce, Core2Duo/965p.
The problem is when I press power off button on the case, it pops with shut down menu instead of shutting down like it supposed to do in first place (if I wanted to go through confirmation menu I would do so, when I use the power off button I don't want it to ask me what I want to do).
How to fix the problem?

Thanks.

Sergei.

---

### Post by SergeiFranco on 2007-12-25
Update: when I installed and ran kpowersave - it shutdown properly with power button.
So I assume there is a setting somewhere....

Another question how do I turn on the numlock by default on login manager?

---

### Post by SergeiFranco on 2007-12-25
I found the culprit:
/etc/acpi/powerbtn.sh
This is the corrected version of the file, I was lazy so instead of changing whole if else I jsut changed 1 number 1 to 0 in 

```
    if [ $KDESES -eq 1 ] ; then
        # single KDE session -> ask user
        /usr/bin/dcop --all-sessions --all-users ksmserver ksmserver logout 0 2 0
        exit 0
    else

```
This is the whole file
```
#!/bin/sh
# /etc/acpi/powerbtn.sh
# Initiates a shutdown when the power putton has been
# pressed.

# Skip if we just in the middle of resuming.
test -f /var/lock/acpisleep && exit 0

# If gnome-power-manager, kpowersave or klaptopdaemon are running, let
# them handle policy This is effectively the same as 'acpi-support's
# '/usr/share/acpi-support/policy-funcs' file.

if pidof gnome-power-manager kpowersave > /dev/null ||
  (pidof dcopserver > /dev/null && test -x /usr/bin/dcop && /usr/bin/dcop kded kded loadedModules | grep -q klaptopdaemon) ; then
    exit
fi

# Otherwise, if KDE is found, try to ask it to logout.
# If KDE is not found, just shutdown now.
if ps -Af | grep -q '[k]desktop' && pidof dcopserver > /dev/null && test -x /usr/bin/dcop ; then
    KDESES=`pidof dcopserver | wc -w`
    if [ $KDESES -eq 1 ] ; then
        # single KDE session -> ask user
        /usr/bin/dcop --all-sessions --all-users ksmserver ksmserver logout 0 2 0
        exit 0
    else
        # more than one KDE session - just send shutdown signal to all of them
        /usr/bin/dcop --all-sessions --all-users ksmserver ksmserver logout 0 2 0 && exit 0
    fi
fi

# If all else failed, just initiate a plain shutdown.
/sbin/shutdown -h now "Power button pressed"
```

---

