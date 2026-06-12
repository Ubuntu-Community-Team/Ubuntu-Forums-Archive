---
title: "CRON job not running"
date: 2014-07-03
forum: General Help
---

### Post by Luft on 2014-07-03
I have a script that i need to run as the root user.

The script (It's quick and dirty so be gentle):
=============================
#!/bin/bash
rm /home/user/scripts/BadBoyList
cd /var/log/apache2
cat access.log | grep -v 192.168.1 | grep 'HTTP/1.1" 403' > /home/user/scripts/BadBoyList
rm /home/user/scripts/BadBoyIP
egrep --only-matching -E  '(25[0-5]|2[0-4][0-9]|[01]?[0-9][0-9]?)\.(25[0-5]|2[0-4][0-9]|[01]?[0-9][0-9]?)\.(25[0-5]|2[0-4][0-9]|[01]?[0-9][0-9]?)\.(25[0-5]|2[0-4][0-9]|[01]?[0-9][0-9]?)' /home/user/scripts/BadBoyList | sort | uniq > /home/user/scripts/BadBoyIP
cat /home/user/scripts/BadBoyIP >> /home/user/scripts/BadBoyHistory
rm /home/user/scripts/BadBoyHistory2
mv /home/user/scripts/BadBoyHistory /home/user/scripts/BadBoyHistory2
cat /home/user/scripts/BadBoyHistory2 | sort | uniq > /home/user/scripts/BadBoyHistory
iptables -F
while read IP; do iptables -A INPUT -s "$IP" -j DROP; done < /home/user/scripts/BadBoyHistory

==============================
It scans my web access log for an error 403 (forbidden) and blocks that IP address in my iptables.  It works if I run it in a terminal as sudo but it fails to run as a cron job.

I edited the cron table thus: sudo crontab -e
I then added the line: */1 * * * * /home/user/scripts/find403.sh 2>&1 /tmp/testlog.log

The /tmp/testlog.log is never created and my iptables remain unchanged.

I added the test line:*/1 * * * * echo "I'm working" >> /home/user/scripts/test.txt
That file gets created and added to each minute so I know that the cron jobs are being run.

I have ensured that the find403.sh file has the permissions of 755 so it is executable. 

I've tried everything that I can think of.  What have I missed?

EDIT:
I ran one more test.  I flushed the iptables, then I deleted all of the temp files and waited.  The temp files were created and the iptables remained empty.  This tells me that the script is actually running but can not execute the one line that modifies the iptables.

i.e. **while read IP; do iptables -A INPUT -s "$IP" -j DROP; done < /home/user/scripts/BadBoyHistory** cannot be executed if the cron job starts the script but can be executed if I run the script using the sudo command.

What's up with that?!

---

### Post by ubudog on 2014-07-03
Only thing I can think of is putting 'sh' in front of /home/user/scripts/find403.sh 2>&1 /tmp/testlog.log.

---

### Post by steeldriver on 2014-07-03
Try adding the full path to the iptables binary (it's probably in /sbin - but check with 'which iptables')

```

while read IP; do [COLOR=#0000ff]**/sbin/iptables**[/COLOR] -A INPUT -s "$IP" -j DROP; done < /home/user/scripts/BadBoyHistory

```

Anything run from cron inherits a very limited environment

---

### Post by Luft on 2014-07-03
Thanks ubudog.  That gave me a glimmer of hope but alas ... :(

It's like the iptables command won't run as the root user under cron but will run under sudo.  Too weird.

---

### Post by Luft on 2014-07-03
Touchdown!!!!!!
Thank you steeldriver!! :p

Edit:
Just one more thing for anyone else using cron.  I had to give the full path to sort and uniq as well.  These were used in a couple of places in the script.

---

### Post by SeijiSensei on 2014-07-03
> **Luft said:**
> Touchdown!!!!!!

I believe the proper term at the moment is Gooooooal!.

---

### Post by Luft on 2014-07-03
I spoke too soon.  I'm not quite out of the woods.  The iptables grow and grow and grow...

The uniq process is suppose to only allow unique entries but fails to work when run from cron.  I set the full path (/usr/bin/uniq) and it works when run from a shell using sudo but apparently doesn't when run from cron.

I'm wondering if the uniq executable uses something else in another location that cron doesn't know about?

This has officially become a pain.

Edit: Never mind.  I forgot to use the full iptables path when flushing the rules.  :redface:

It's all good now!

---

