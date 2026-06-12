---
title: "TRAP stopped working about upgrading to Lubuntu 17.04 &quot;Zesty Zapus&quot; - Release amd64"
date: 2017-12-11
forum: General Help
---

### Post by nzdreamer55 on 2017-12-11
Hi everyone,

I had this little script that would run via cronjob.  The job sometimes can take a long time and I don't want the cronjob to start another if the first instance has not finished so I am using this trap.  It was working fine until I upgraded to 17.04.  Now the trap file, in this case called TV.lock, never gets removed so it runs once and then never again unless I delete the file TV.lock.

I am not well versed in linux so any help and with as much hand holding is much appreciated.

Thanks.

Steve

```
#!/bin/bash

trap "rm -f /home/linux/TV.lock" SIGINT SIGTERM


if [ -e /home/linux/TV.lock ]
then
  echo "TV.Synctorrent is running already."
  exit 1
else


  touch /home/linux/TV.lock


filebot -script fn:amc "/media/linux/1TB.Scratch/TV" --def "unsortedFormat=/home/windowsshare/Om/Unsorted/{fn}.{ext}" --def "seriesFormat=/media/windowsshare/Series.Pool/{az}/{n.replaceFirst(/^(?i)(The|A|An)\s(.+)/, /\$2, \$1/)}/{episode.special ? 'Special' : 'Season '+s.pad(2)}/{n}.{s00e00}{'.'+fn.match(/(?i:proper)/).toLowerCase().upperInitial()}{'.'+fn.match(/(?i:repack)/).toLowerCase().upperInitial()}{'.'+[vf]}{'.'+[vc]}{'.'+[ac]}{'.'+[af]}{'.'+[source]}{'.'+[group]}.{t}" -r --log-file "/home/linux/log/filebot.TV.log" --action copy --conflict auto -non-strict --def backdrops=y --def subtitles=en --def artwork=y  --def clean=y --def ut_label=tv --def excludeList="/home/linux/log/exclude/filebot.input.tv"


  rm -f /home/linux/TV.lock
  exit 0


fi
```

---

