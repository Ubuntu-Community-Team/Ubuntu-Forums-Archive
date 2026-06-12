---
title: "Help with crontab"
date: 2013-11-23
forum: General Help
---

### Post by Thimoteus on 2013-11-23
I'm trying to run
```
xbacklight -get > test.txt
```
every minute, but every way of doing this as a cron job doesn't seem to work. I've tried putting it into a script, setting the path variable in the cron file and the script, setting the shell variable, calling xbacklight with its absolute path, and nothing seems to work. In every case the cron job will write a file, but with nothing inside. Any ideas?

---

### Post by steeldriver on 2013-11-23
Are you setting the DISPLAY environment variable in your cron command / script? otherwise xbacklight will produce just an error (which will go to stderr not stdout, so won't be captured in your file)

```

$ echo $DISPLAY
:0.0
$ 
$ xbacklight -get
100.000000
$ 
$ DISPLAY= xbacklight -get
Cannot open display ""

```

---

### Post by Thimoteus on 2013-11-23
It worked! Thanks!

My new crontab line is:
```

* * * * * export DISPLAY=:0 && /usr/bin/xbacklight -get > test.txt

```

---

