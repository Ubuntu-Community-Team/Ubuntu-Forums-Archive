---
title: "sox failing to execute as a cron entry while another sound app running"
date: 2014-06-09
forum: General Help
---

### Post by Hiflux_Seven on 2014-06-09
A trivial application, but somthing that worked fine under 10.04 and fails under 14.04.

sox (play) is configured via my user crontab to chime a cuckoo clock sound hourly:
0 * * * *       play -q -v 0.25 /home/username/cuckoo.au

The soundfile plays normally unless another sound application is running simultaneously such as vlc or rhythmbox, in which case syslog still logs a successful execution of play but no sound output occurs.  If I run play manually, if works fine-- even with the other application(s) running.  Executed from cron and it fails to produce the expected sound.

I just upgraded from 10.04, and the exact same configuration worked fine.

Any idea what's going on?

---

### Post by Habitual on 2014-06-09
full /path/to/play ?

---

### Post by Hiflux_Seven on 2014-06-09
Tried including /usr/bin/play full path with same results.  Something really odd, if I pause a playing file say at 1:00:20, the cuckoo.au from cron will at that time play like it's been queued from it's scheduled time of 1:00:00. If the playing file is not paused or stopped, the cuckoo from cron never plays.

---

### Post by Hiflux_Seven on 2014-06-09
In addition, I tried placing the command in root's crontab with exactly the same results.  No play if another sound application is running.  Syslog shows the 'play' command get executed via cron at the proper time, but no sound is output.

---

### Post by Habitual on 2014-06-09
I'm stuck, sorry.

---

### Post by Hiflux_Seven on 2014-06-10
[COLOR=#000000]exporting the DISPLAY variable within the crontab entry solved the problem. No idea why, but it works.[/COLOR]

[COLOR=#000000]the crontab entry now reads:[/COLOR]
[COLOR=#000000]0 * * * * export DISPLAY=:0 && /usr/bin/play -q -v 0.25 /home/usr/cuckoo.au[/COLOR]

[COLOR=#000000]With the DISPLAY variable included, play (sox) outputs the cuckoo.au sound regardless of whether another sound application is executing concurrently on the desktop.[/COLOR]

---

### Post by Habitual on 2014-06-10
good job!
Glad it worked out.

---

