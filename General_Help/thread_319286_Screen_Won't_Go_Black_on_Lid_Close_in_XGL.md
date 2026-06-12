---
title: "Screen Won't Go Black on Lid Close in XGL"
date: 2006-12-15
forum: General Help
---

### Post by web250 on 2006-12-15
I just installed XGL yesterday, works awesome, looks great. (I can't do AIGLX, I have a x1300 ATI).

But now when I close my screen (Dell e1505 lappy) it doesn't go black. I don't want to burn out my backlight.

Fix?

---

### Post by web250 on 2006-12-15
bump

---

### Post by web250 on 2006-12-15
bumpity bump

---

### Post by NTolerance on 2006-12-18
Back up your /etc/acpi/lid.sh file and replace it with this:

```
#!/bin/sh

. /usr/share/acpi-support/power-funcs
. /etc/default/acpi-support

[ -x /etc/acpi/local/lid.sh.pre ] && /etc/acpi/local/lid.sh.pre

grep -q closed /proc/acpi/button/lid/*/state
if [ $? = 0 ]
then
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
                su $user -c "xscreensaver-command -unthrottle"

            fi
            if [ x$RADEON_LIGHT = xtrue ]; then
                [ -x /usr/sbin/radeontool ] && radeontool light on
            fi
            su $user -c "xscreensaver-command -deactivate"
            su $user -c "xset dpms force on"
        fi
    done
fi
[ -x /etc/acpi/local/lid.sh.post ] && /etc/acpi/local/lid.sh.post

```

---

### Post by H.E. Pennypacker on 2007-01-17
> **NTolerance said:**
> Back up your /etc/acpi/lid.sh file and replace it with this:

```
#!/bin/sh

. /usr/share/acpi-support/power-funcs
. /etc/default/acpi-support

[ -x /etc/acpi/local/lid.sh.pre ] && /etc/acpi/local/lid.sh.pre

grep -q closed /proc/acpi/button/lid/*/state
if [ $? = 0 ]
then
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
                su $user -c "xscreensaver-command -unthrottle"

            fi
            if [ x$RADEON_LIGHT = xtrue ]; then
                [ -x /usr/sbin/radeontool ] && radeontool light on
            fi
            su $user -c "xscreensaver-command -deactivate"
            su $user -c "xset dpms force on"
        fi
    done
fi
[ -x /etc/acpi/local/lid.sh.post ] && /etc/acpi/local/lid.sh.post

```

Does this work for someone who is not using XGL or AIGLX?

---

### Post by NTolerance on 2007-01-18
I don't see any reason why it wouldn't.  As long as you back up your original lid.sh file you can't do any harm by trying it out.

---

### Post by jvaudrey on 2007-12-08
Just a quick message to say thats for the new lid.sh script it works perfect 
Thanks

John

---

### Post by mk4umha on 2007-12-12
Awesome, that worked like a charm on my Dell M1210. Thanks,

---

### Post by usergroup81 on 2007-12-20
Thanks, that worked for me Dell E1505.

---

