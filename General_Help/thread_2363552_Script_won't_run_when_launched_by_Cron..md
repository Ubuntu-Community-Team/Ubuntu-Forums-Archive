---
title: "Script won't run when launched by Cron."
date: 2017-06-11
forum: General Help
---

### Post by nzdreamer55 on 2017-06-11
Hello,

I have  a script that works when I call it from a terminal window, however when I edit my crontab-e (I have edited but using sudo and non-sudo) it does not seem to work.  I have checked the /var/logs/syslog and get stuff like this

```
Jun 11 11:55:01 linuxlaptop CRON[1901]: (linux) CMD (/home/linux/Script/get.tv.new)Jun 11 11:55:01 linuxlaptop CRON[1900]: (root) CMD (get.tv.new)
Jun 11 11:55:01 linuxlaptop CRON[1899]: (CRON) info (No MTA installed, discarding output)
Jun 11 11:55:01 linuxlaptop CRON[1898]: (CRON) info (No MTA installed, discarding output)
Jun 11 11:56:01 linuxlaptop CRON[1905]: (linux) CMD (/home/linux/Script/get.tv.new)
Jun 11 11:56:01 linuxlaptop CRON[1906]: (root) CMD (get.tv.new)
Jun 11 11:56:01 linuxlaptop CRON[1904]: (CRON) info (No MTA installed, discarding output)
Jun 11 11:56:01 linuxlaptop CRON[1903]: (CRON) info (No MTA installed, discarding output)

```

I changed the crontab to the following
```
*/1 * * * * get.tv.new &>> /home/linux/cron.log 2>&1


```
But all that does is create an empty file when the job runs.

I'm not sure where to go from here to trouble shoot the issue.  Any help is greatly appreciated.

Steve

---

### Post by cariboo on 2017-06-11
It might help if you showed us the script.

---

### Post by nzdreamer55 on 2017-06-11
Sure.  Here are the scripts.  Remember that when I run the script tv.get.new in a terminal window it works.

tv.get.new calls 2 different scripts

```
#!/bin/bash
TV.lftp.sync.sh
tv.copy.script.new
```



TV.lftp.sync.sh
```
#!/bin/bash

login=XXXXXXXX
pass=XXXXXXXXX
host=XXXXXXXXXX
remote_dir=/downloads/finished/TV
local_dir=/media/linux/1TB.Scratch/




trap "rm -f /tmp/TV.synctorrent.lock" SIGINT SIGTERM


if [ -e /tmp/TV.synctorrent.lock ]
then
  echo "TV.Synctorrent is running already."
  exit 1
else


  touch /tmp/TV.synctorrent.lock


  lftp -d -u $login,$pass $host << EOF
  set ftp:ssl-allow no
  set mirror:use-pget-n 5
  mirror -c -P5 --loop --log=/home/linux/synctorrents.TV.log $remote_dir $local_dir
  quit
EOF


  rm -f /tmp/TV.synctorrent.lock
  exit 0


fi
```

tv.copy.scrpit.new

```
#!/bin/bash#/usr/local/bin/solo -port=3000 


trap "rm -f /tmp/TV.synctorrent.lock" SIGINT SIGTERM


if [ -e /tmp/TV.synctorrent.lock ]
then
  echo "TV.Synctorrent is running already."
  exit 1
else


  touch /tmp/TV.synctorrent.lock


filebot -script fn:amc "/media/linux/1TB.Scratch/TV" --def "seriesFormat=/media/windowsshare/Series.Pool/{az}/{n.replaceFirst(/^(?i)(The|A|An)\s(.+)/, /\$2, \$1/)}/{episode.special ? 'Special' : 'Season '+s.pad(2)}/{n}.{s00e00}{'.'+fn.match(/(?i:proper)/).toLowerCase().upperInitial()}{'.'+fn.match(/(?i:repack)/).toLowerCase().upperInitial()}{'.'+[vf]}{'.'+[vc]}{'.'+[ac]}{'.'+[af]}{'.'+[source]}{'.'+[group]}.{t}" -r --log-file "/home/linux/log/filebot.log" --action copy --conflict auto -non-strict --def backdrops=y --def subtitles=en --def artwork=y --def clean=y --def ut_label=tv --def excludeList="/home/linux/log/filebot.input.tv" | timestamp >> /home/linux/log/filebot.tv.copy.log 2>&1 


  rm -f /tmp/TV.synctorrent.lock
  exit 0


fi
```

So I can get all of these to work if I run them from the terminal window, but not if cron runs them.  I run them by typing in tv.get.new into bash terminal window.

---

### Post by steeldriver on 2017-06-11
```

&>>

```

is a bashism - although the script you have written will run in bash, AFAIK the cron command itself will be run by POSIX sh (which will likely treat it to mean "run get.tv.new in the background, and append nothing to /home/linux/cron.log")

Also it's always best to give full paths rather than relying on cron's limited environment

```

[COLOR=#0000ff]*[/COLOR] * * * * [COLOR=#0000ff]/path/to/[/COLOR]get.tv.new [COLOR=#0000ff]>[/COLOR] /home/linux/cron.log [COLOR=#0000ff]2>&1[/COLOR]

```

You *may *need to add a PATH= statement *inside *your get.tv.new script (or use full paths there as well) - unless all the programs it calls are in cron's default /usr/bin or /bin

---

### Post by nzdreamer55 on 2017-06-11
ok so I change the crontab to read

```
*/1 * * * * /home/linux/Script/get.tv.new
```

so the path is included.  This path is also set in the bash environment but like you said maybe it isn't running in bash

I have changed the get.tv.new script to contain paths as well.

```
#!/bin/bash

/home/linux/Script/TV.lftp.sync.sh
/home/linux/Script/tv.copy.script.new



```

I think that might have been the answer.  Will know in a few hours.  Thanks.

---

