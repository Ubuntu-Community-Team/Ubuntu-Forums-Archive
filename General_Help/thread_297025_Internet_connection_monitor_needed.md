---
title: "Internet connection monitor needed"
date: 2006-11-10
forum: General Help
---

### Post by JimS on 2006-11-10
...
I believe that my ISP (3 MB cable) is failing to provide connection 24/7.
There seems to be service outages.
I lose VoIP (Lingo) in the middle of a call, which is a big pain.

My old Linksys cable modem would stop and not reset itself.
I would have to cold boot it and it might go down again in a few minutes.

I just bought a new D-Link cable modem and
so far it resets itself after an outage.

I have TV service on the same cable, by the same company,
and no TV problems.

I thought it might be the gadget in the telephone pole switchbox
my ISP uses to select the type of cable
service they provide to my house.

***
What I would like is some monitoring software which would tell me
when the connection is on and when it is off.
Then I can properly report breaks in service to my ISP.
***

Any ideas?

Running Breezy on an old Dell 4100 desktop, 512 RAM, dual boot,
which I leave on 24/7.

Thanks in advance.
...

---

### Post by der_joachim on 2006-11-10
If you use KDE, try knemo. 
Additionally, both Gnome and KDE have widgets in which your Ethernet status is shown. KDE has Superkaramba and one such widget is called Aero AIO. 

ATM, I have a very simple system monitor called conky. You can find more info in this forum. It is quite popular. 

Hope this helps.

---

### Post by JimS on 2006-11-10
...

Thanks,

Using Gnome.

I want the software to record when I'm up and when I'm down,
or perhaps just when I go down and for how long.

...

---

### Post by krismatth3 on 2006-11-10
Maybe a simple script would do:

```

#!/bin/sh

HOST=google.com            # host to spam ping
FAILLOG=fail_log.txt       # file to log failures to
TMPFILE=/tmp/conn_monitor  # temporary file
INTERVAL=30                # how often to ping, in seconds

append_log()
{
    OLDIFS=$IFS
    IFS=$
    for LINE in `cat -E $TMPFILE`; do
        LINE=`echo $LINE | tr -d "\n"`
        echo "    " $LINE >> $FAILLOG
    done
    IFS=$OLDIFS
}

while [ 1 ]; do
    ping -c 4 $HOST &> $TMPFILE
    if [ $? -eq 0 ]; then
        echo "PING SUCCESS at "`date`"."
    else
        echo "PING FAILURE at "`date`"."
        # we failed, so run a traceroute for diagnostic purposes
        traceroute $HOST 1>> $TMPFILE 2>&1
        echo "PING FAILURE at "`date`"." >> $FAILLOG
        append_log
    fi
    sleep $INTERVAL
done

```

This will run a traceroute (so you must "apt-get install traceroute" if you haven't already) whenever the ping fails, to give you some hope of diagnosing the problem.

---

### Post by JimS on 2006-11-10
...
Hey thanks for the code.
I haven't coded for 20 years.
Used to do COBOL, Fortran, JCL, Forth, Basic, a bit of Pascel, etc.
This looks a bit like Pascel.

I've never written a script for Linux,
but I'm sure I can find out how easy enough.
I'll research on this in a day or 2.
I'm real busy with my new busines and a broken transportation issue.

Very interesting.

Thanks again.
...

---

