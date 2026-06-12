---
title: "No MTA installed, discarding output"
date: 2014-03-27
forum: General Help
---

### Post by vasa1 on 2014-03-27
My crontab looks like this:

```
28 * * * * /home/vasa1/bin/rsync-sound
29 * * * * /home/vasa1/bin/rsync-info
30 * * * * bash -c 'rsync -lrtv --delete --protect-args --modify-window=1 --files-from=/home/vasa1/Dropbox/rsync-include.txt / /media/vasa1/TOSHIBA\ EXT/BACKUP/ &> /home/vasa1/"$(date +\%I_\%M)"rsync.log'

```

And /home/vasa1/bin/rsync-sound is this:
```
#!/usr/bin/env bash

for i in {1..5}; do mplayer -really-quiet /usr/share/sounds/freedesktop/stereo/complete.oga ; done
```

And /home/vasa1/bin/rsync-info is this:
```
#!/usr/bin/env bash

zenity --info --display=:0.0 --timeout=5 --text="rsync runs \nin \ntwo min!"

```
By testing, I know that it is the execution of **rsync-sound** and not the other two that causes /var/log/syslog to show this:
```
Mar 27 16:24:07 vasa1-Inspiron-1545 CRON[2497]: (CRON) info (No MTA installed, discarding output
```

When I run *mplayer -really-quiet /usr/share/sounds/freedesktop/stereo/complete.oga* from a terminal, there's no output (errors/messages/warnings) other than the sound.

So why does *cron* seem to generate some output and want to mail it to me for this specific crontab entry?

---

