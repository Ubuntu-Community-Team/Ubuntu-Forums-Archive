---
title: "[SOLVED] Need help making a cron script to check/re-activate Interent connection"
date: 2007-09-22
forum: General Help
---

### Post by kvonb on 2007-09-22
My server connects to the Internet using pppoe, and it works well apart from when my ISP has problems.

The connection goes up and down some days and the pppoe daemon gives up the ghost if it can't get a re-connection within a few tries.

Sometimes the net is down for a whole day and I have to physically find and kill the pppoe process and restart it.

I would like to have a cron script that pings my ISP every few minutes and if there is no response, kills and re-starts the connection.

I have no idea where to start and would appreciate some help.

Thanks, KEv :).

---

### Post by Bachstelze on 2007-09-22
Could be something like :

```
if ! ping www.somehost.com; then
    your commads here
fi
```

---

### Post by kvonb on 2007-09-22
Thanks for the quick reply :).

How does this look as a shell script?

```
#!/bin/bash
if ! ping myisp.com; then
   killall pppd
   pon dsl-provider
fi
```

I'm not sure if I need the semi-colon, or where though.

And I can't test it at the mo because my wife is using Skype :(.

---

### Post by kvonb on 2007-09-22
I put that lot into an executable script and put he script in /sbin/.

I added a cron job using webmin and this is the output from crontab -l:

```
root@server:/etc/cron.d# crontab -l

0 * * * * /etc/webmin/bandwidth/rotate.pl
@monthly rm -rf /var/log/*.gz #Delete old logs every month
10 * * * * /sbin/nettest.sh #Keeps the Interent alive

root@server:/etc/cron.d#
```I killed the connection and waited for ten minutes (I believe I set it to activate every 10 mins!) but nothing happened.

Any ideas?

EDIT*  I ran the script on the command line and it worked, then I edited the script after reading through man crontab to put a semicolon at the end of each command, rescheduled it and ran it directly from within webmin and it ran.  I also read that the log is sent to syslog, ie: tail -F /var/log/syslog.

All works well now, thanks :).

---

### Post by kvonb on 2007-09-23
Well, did I stuff up BIG time!!!!!

The script worked, but my big mistake was the ping command.  The real command should be 

```
**ping -c1 myisp.com**
```not simply:

```
ping myisp.com
```The ping command keeps running until the connection dies, then the connection is restarted and **another** ping process starts up, and the old one keeps going :S.

I have now been flood pinging my ISP for over 12 hours, my server's hard disk was filled to capacity by log files and emails to the sysadmin, and there were about 30 ping processes running!!!!

Plus I just wasted about 1.2 gigs of my monthly data quota on pings!

So the script now looks like this:

```
#!/bin/bash
if ! ping -c 1 myisp.com. >/dev/null; then
   killall pppd;
   pon dsl-provider;
fi
```Note the ***> dev/null*** part, that stops the output of ping going into /var/log/syslog, therefore preventing the email every time the cron job runs.

Ah to live and learn from our mistakes :).

---

