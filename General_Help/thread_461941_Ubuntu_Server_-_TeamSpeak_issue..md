---
title: "Ubuntu Server - TeamSpeak issue."
date: 2007-06-02
forum: General Help
---

### Post by Jo0Lz on 2007-06-02
Hey guys/girls.

I had an issue with my TeamSpeak server. It runs on my Ubuntu server box (Feisty).
All is well, the whole server installation was a breeze! Only thing that I needed to set up locally was SSH, after that remote configuration was easy. Adding packages, installing webmin, etc.

But, I've got a TeamSpeak server, running on it right now. All is well, but I want the TeamSpeak server to start itself when the server goes down for whatever reason (Power out, crash, whatever...)

I'm running the Server under user TSS.
Set up cronjob for TSS (while being root, 'su tss' -> then 'sudo crontab -e' to edit the cronjob for TSS.)
It says this:
```
# m h  dom mon dow   command
@reboot /home/tss/tss2_rc2/cronscript

```

The cronscript is executable (by tss, and chmodded 755 - created the file, then 'chmod 755 cronscript' - chmod +x cronscript)
It's content:
```

#!/bin/sh
cd /home/tss/tss2_rc2/
if /home/tss/tss2_rc2/teamspeak2-server_startscript status == "the server seems to be running" > /dev/null
then
exit
else
/home/tss/tss2_rc2/teamspeak2-server_startscript start
fi

```

I picked that up from another forum, can't find it again though  :')
After that, I scripted the check for the .pid file, since power outage doesn't throw that file away.
I edited: 'sudo vim /etc/rc.local'
And the file now says:
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

if [ -f /home/ts/tss2_rc2/tsserver2.pid ]
then
echo "removing /home/ts/tss2_rc2/tsserver2.pid"
rm -f /home/ts/tss2_rc2/tsserver2.pid
fi

exit 0

```

If all was well, on reboot, the server will come up!

Jo0Lz.

---

### Post by Jo0Lz on 2007-06-02
Oh.

Whilst posting this, I concluded that the home dir's that i've provided in the script are missing the latter s.
(ts, whilst it should be tss.)

I'll change that now, see if that helps.

:'), sometimes just reviewing the steps one did, is enough to find errors.

/me kicks himself in the head.

---

### Post by Jo0Lz on 2007-06-02
Ok. Hahahaha, well, seems I've solved my own problem.
Setting the right directory helps a lot, so it seems. The server rebooted nicely.
Only thing that I didn't check right now, is if the .pid file is deleted if it exists.

It didn't, because it was a proper shutdown, so the server came up nicely.
Maybe someone can use this as a tutorial now!?!

---

### Post by waynemr on 2007-07-25
I gave this a whirl and something doesn't appear to be happening right.

I put my teamspeak files in /etc/teamspeak
I have a user and group called teamspeak
I did chown -R teamspeak:teamspeak /etc/teamspeak
I edited crontab for teamspeak to run /etc/teamspeak/cronscript
I did chmod 755 and +x to /etc/teamspeak/cronscript 
I used your code above, changed for my username and directories...

But upon reboot the teamspeak server doesn't load. Is there anything special configured for your TSS account?

I saw a bug about crontab that indicated that the default editor, nano, doesn't produce a new line at the end of the file by default - so for my crontab I hit Enter twice after putting in the @reboot /etc/teamspeak/cronscript line. Could that be hosing it (too many new lines)?

Thanks! I've been scratching my head over how to use cron with teamspeak for a couple of hours, because I want it to autostart with an account other than root.

---

### Post by trent dillman on 2007-07-25
...

---

