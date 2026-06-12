---
title: "Alarm Clock Apps?"
date: 2006-10-19
forum: General Help
---

### Post by wolf202 on 2006-10-19
I'm having trouble finding a alarm clock app that will play a mp3 or ogg or wav, whatever, at a certain time.  Any suggestions?

-wolf

---

### Post by ubuntuuser on 2006-10-20
I like sanduhr a lot, give it a go.

---

### Post by cody50 on 2006-10-20
I have a cool plugin for XMMS that acts as an alarm clock. it works pretty slick. I forget where i found it, but searching somethign like xmms alarm plugin should work.

---

### Post by bruenig on 2006-10-20
I use cron and have it launch an .ogg file at a certain time.

Took me a while to figure it out, but it can be found here.
[http://en.wikipedia.org/wiki/Crontab](http://en.wikipedia.org/wiki/Crontab)

For ubuntu, I just added my username to the file /etc/cron.allow.
```
sudo gedit /etc/cron.allow
``` Add your username and then save.

After you do that you can do
```
crontab -e
```

Following the syntax from wikipedia have it launch a media file with totem or something. My crontab looks like this
```

# m h  dom mon dow   command
31 6 * * 1-5 /usr/local/bin/alarm
```
Note this means that at 6:31 on every day monday-friday it runs /usr/local/bin/alarm.
Where /usr/local/bin/alarm is a script that reads this.
```

#! /bin/bash
DISPLAY=:0 /usr/bin/totem /home/bruenig/files/media/audio/alarm.ogg

```
Which calls upon totem to launch alarm.ogg.

Maybe a bit more complex than what you were looking for but it is an option.

---

### Post by brian g on 2006-11-16
> **ubuntuuser said:**
> I like sanduhr a lot, give it a go.

how do i get rid of that app?
when i attempt to remove the package i get an error
```
E: sanduhr: subprocess pre-removal script returned error exit status 2


```

---

### Post by stylishpants on 2006-11-16
A lighter alternative to cron is "at".  ("man at" for details.)

Cron is used to set recurring events.  "at" is used to set a one-time event.

It works like this:

```

fraser@ged:~$ at now + 6 min
warning: commands will be executed using /bin/sh
at> xmms --play
at>             # <-- press Ctrl-D here to stop entering commands
job 3 at Wed Nov 15 23:32:00 2006

```


Or, you can specify an absolute time instead of a relative one:
```

fraser@ged:~$ at 9:30 pm
warning: commands will be executed using /bin/sh
at> xmms --play
at>             # <-- press Ctrl-D here to stop entering commands
job 4 at Thu Nov 16 09:30:00 2006

```

Note that if you just say "9:30" instead of "9:30 pm", you will get 9:30 am.  "at" assumes that times are in 24 hour format unless you specify "am" or "pm".

Anyway, at and cron are nice because you can use them to drive whatever player you happen to prefer (or just use "mpg321" or "ogg123" or "flac123" to play without an external player.)

To find out what command line flags to use to start your player, read it's man page (eg. man amarok) or just try the --help flag (eg. amarok --help)

---

