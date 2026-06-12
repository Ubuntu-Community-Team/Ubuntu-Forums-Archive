---
title: "Help to cron kill process"
date: 2015-06-21
forum: General Help
---

### Post by Bromden on 2015-06-21
Hi all, I've an annoying problem with Spotify. It repeatedly starts a process called SpotifyHelper that eats a lot of CPU and heats up the computer...if I kill the process, CPU usage returns normal and Spotify still works correctly, so I would ask if someone can help me creating a crontab to kill the SpotifyHelper process every 5min.
I could do it by myself the problem is that the process changes the PID everytime it gets killed...

;)

---

### Post by Habitual on 2015-06-21
something like this?
```
SERVICE='spotifyhelper'
 
if /usr/bin/pgrep $SERVICE > /dev/null
then
    exit 0 
else
    killall -9 "$SERVICE"
    exit 1
fi
#EOF
```

cron:
```
*/5 * * * * /path/to/script.sh
```

---

### Post by Bromden on 2015-06-21
Thank you, you answered very fast :)

I just made a little change to the script this way:

```
SERVICE='SpotifyHelper'
 
if /usr/bin/pgrep $SERVICE > /dev/null
then
    exit 0 
else
    pkill "$SERVICE"
    exit 1
fi
#EOF
```

Seems to works nicely, I just have to warn that killing the Helper sometimes Spotify is unable to show the internal browser.

):P

---

### Post by bapoumba on 2015-06-21
This is a year old, but may be something you can use, in particular in the last post : [https://community.spotify.com/t5/Help-Desktop-Linux-Mac-Windows/0-9-4-183-g644e24e0-SpotifyHelper-is-causing-very-high-disk/td-p/723889](https://community.spotify.com/t5/Help-Desktop-Linux-Mac-Windows/0-9-4-183-g644e24e0-SpotifyHelper-is-causing-very-high-disk/td-p/723889)

---

