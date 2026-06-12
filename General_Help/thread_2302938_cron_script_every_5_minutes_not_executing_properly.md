---
title: "cron script every 5 minutes not executing properly"
date: 2015-11-14
forum: General Help
---

### Post by Berduchwal on 2015-11-14
Hi

Following script
```
line1=$(head -n 1 /sys/bus/w1/devices/28-03157440c8ff/w1_slave | cut -c 37-)
        line2=$(tail -n 1 /sys/bus/w1/devices/28-03157440c8ff/w1_slave | cut -c 30-)
        if [ "$line1" = "YES" ]
        then
        marker=1
        else
        marker=0
        fi
        echo  "INSERT INTO temperature (readingstamp,location,instrument,valid,value) VALUES ('$(date +%Y-%m-%d) $(date +%T)',2,1,'$marker','$line2');" | mysql -u temscript -ptest weather
```

Is running without output or problems with:
```
sh temread.sh
```

But with crontab -e
```
*/5 * * * * /usr/bin/sh /home/me/Documents/Temperature/temread.sh
```

I get the following: tail /var/log/syslog
```
CRON[19889]: (me) CMD (/usr/bin/sh /home/me/Documents/Temperature/temread.sh )
CRON[19882]: (CRON) info (No MTA installed, discarding output)
```

I am guessing that I need for reformat bash script for cron purposes but I do now know how can I debug it. As it shows no bugs using standard sh command.

Any help with this will be appreciated.

---

### Post by ian-weisser on 2015-11-14
Have you tried using full paths for each command? (head, tail, echo, date, mysql, etc.)
Cron does not run as you, and runs in a very limited environment.

---

### Post by SeijiSensei on 2015-11-14
The error means that the script generates output, but cron has no place to send it to.  The default is to mail the results to the script's owner, but if you don't have a mail program ("MTA") like Postfix or sendmail, it cannot be sent.  The best solution is to route the output to a log file like this:
```
*/5 * * * * /usr/bin/sh /home/me/Documents/Temperature/temread.sh >> /path/to/some/file
```
The log file has to be located in a directory that the script's owner can write to.

---

### Post by Berduchwal on 2015-11-15
Modified as suggested:
```
line1=$(/usr/bin/head -n 1 /sys/bus/w1/devices/28-03157440c8ff/w1_slave | /usr/bin/cut -c 37-)
line2=$(/usr/bin/tail -n 1 /sys/bus/w1/devices/28-03157440c8ff/w1_slave | /usr/bin/cut -c 30-)
if [ "$line1" = "YES" ]
then
marker=1
else
marker=0
fi
echo  "INSERT INTO temperature (readingstamp,location,instrument,valid,value) VALUES ('$(date +%Y-%m-%d) $(date +%T)',2,1,'$marker','$line2');" | /usr/bin/mysql -u temscript -ptest weather
```

I believe echo and date are part of bash so they do not need a direct link.

It works with simple sh.

Changed crone to:
```
CRON[22002]: (me) CMD (/usr/bin/sh /home/me/Documents/Temperature/temread.sh >> /home/me/Documents/Temperature/log.txt )
CRON[21995]: (CRON) info (No MTA installed, discarding output)

```

Still the same.

I tried following change:
```
(/bin/bash /home/me/Documents/Temperature/temread.sh >> /home/me/Documents/Temperature/log.txt
```

It worked! - Thanks

I changed script to:
```
line1=$(head -n 1 /sys/bus/w1/devices/28-03157440c8ff/w1_slave | cut -c 37-)
line2=$(tail -n 1 /sys/bus/w1/devices/28-03157440c8ff/w1_slave | cut -c 30-)
if [ "$line1" = "YES" ]
then
marker=1
else
marker=0
fi
echo  "INSERT INTO temperature (readingstamp,location,instrument,valid,value) VALUES ('$(date +%Y-%m-%d) $(date +%T)',2,1,'$marker','$line2');" | mysql -u temscript -ptest weather

```

It still worked.

Thank you for your help.

---

### Post by SeijiSensei on 2015-11-15
If the script writes to the "stderr" device as well as "stdout" you need another parameter like this:
```
somescript.sh >> /path/to/some/log 2>&1
```
The "2>&1" tells Linux to redirect stderr to stdout.

---

