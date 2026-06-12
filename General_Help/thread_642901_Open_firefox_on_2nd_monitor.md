---
title: "Open firefox on 2nd monitor?"
date: 2007-12-17
forum: General Help
---

### Post by Nick Payne on 2007-12-17
I have a two monitor setup, and like to run Firefox on the 2nd monitor. However, if I have Firefox running on monitor 2 and close and open it, it always starts up on monitor 1. Other apps such as OpenOffice will open on monitor 2 if they were there when last run, and Firefox on Windows does as well. Is it possible to get Firefox on Ubuntu to do the same? I can't see anything in the Firefox preferences. I'm running Gutsy amd64.

---

### Post by r-mo on 2007-12-17
I don't know whether this will work or not but when running gui apps with crontab you need to tell it which display to use with a command like

```
EXPORT DISPLAY=:0 && /usr/bin/firefox
```

See if it starts on the 2nd display if you change this to DISPLAY=:1

As I say I'm not sure and I'm guessing that as this is an environment variable it will make everything start on DISPLAY :1 after you've run it unless you change it back to DISPLAY :0 by doing 

```
EXPORT DISPLAY=:0
```
in a terminal

---

