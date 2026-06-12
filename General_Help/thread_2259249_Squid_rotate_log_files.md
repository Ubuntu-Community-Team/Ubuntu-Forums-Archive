---
title: "Squid rotate log files"
date: 2015-01-03
forum: General Help
---

### Post by stevenroyals on 2015-01-03
Hi

I read on this site that you have to rotate the log files for squid every day or so.
[http://wiki.squid-cache.org/SquidFaq/SquidLogs](http://wiki.squid-cache.org/SquidFaq/SquidLogs)

When I type in 'squid -k rotate' into the terminal, I got a message saying, command not found did you mean squid3.

I also get a similar message if I put 'sudo' in front of it.

I've also tried putting in 'squid3 -k rotate'. This produces a more extensive error message including, 'cannot write log file /var/log/squid3/cache.log' and 'Permission denied
messages will be sent to 'stderr'.
squid: ERROR: Could not send signal 10 to process 1011: (1) Operation not permitted

I have Ubuntu 14 with squid3 installed.

Thanks
Steve

---

### Post by nerdtron on 2015-01-03
have you tried your command with sudo?

---

### Post by stevenroyals on 2015-01-03
This is what I type and the error I get.

sudo squid -k rotate
sudo: squid: command not found

---

### Post by stevenroyals on 2015-01-03
If I type in

sudo squid3 -k rotate

I get this message which seems to referee to some of my refresh patterns.

2015/01/04 06:39:08| refreshAddToList: Unknown option '-i\.(gif|png|jpg|jpeg|ico)$': override_expire

---

### Post by schragge on 2015-01-03
Try to add a space between -i and regex:
```
refresh_pattern -i[highlight][color=#FFEB90]_[/color][/highlight]\.(gif|png|jpe?g|ico)$
```

---

### Post by stevenroyals on 2015-01-03
I did pick that up and changed it but I still get a similar error message.

squid.conf
refresh_pattern -i \.(gif|png|jpg|jpeg|ico)$ 10080 90% 43200 override_expire ignore-no-cache ignore-no-store ignore-private


I also picked up another error when I posted the line above. I have  'override_expire' instead of  'override-expire'

After saving and restarting squid I now get no error messages when I type in 'sudo squid3 -k rotate"

I assume everything is working correctly and rotating.

Thanks

---

### Post by Holger_Gehrke on 2015-01-03
> **stevenroyals said:**
> 
After saving and restarting squid I now get no error messages when I type in 'sudo squid3 -k rotate"

I assume everything is working correctly and rotating.
Thanks

From the Squid Manual you linked in your original Post:
> 
 To rotate Squid's logs, simple use this command: 

squid -k rotate

For example, use this cron entry to rotate the logs at midnight: 

0 0 * * * /usr/local/squid/bin/squid -k rotate


I understand this to mean that 'squid -k rotate' does **one **rotation. To set it up for automatic daily rotation you have to set up an entry in crontab

---

