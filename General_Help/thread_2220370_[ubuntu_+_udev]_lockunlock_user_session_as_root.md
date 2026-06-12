---
title: "[ubuntu + udev] lock/unlock user session as root"
date: 2014-04-27
forum: General Help
---

### Post by Little_Nooby on 2014-04-27
Good evening,

I'd like to lock/unlock my session using a usb key. Here is what I came to :
```

$ cat /etc/udev/rules.d/logger.rules
ACTION=="add", ENV{ID_FS_UUID}=="E040-9945", RUN+="/usr/bin/gnome-screensaver-command -d"u
ACTION=="remove", ENV{ID_FS_UUID}=="E040-9945", RUN+="/usr/bin/gnome-screensaver-command -l"
```

It didn't work. I test the commands with a terminal and found out the command worked only if runned by the user. As udev's used by root, it explains how my rules didn't work.

I tried this :
```
ACTION=="add", ENV{ID_FS_UUID}=="E040-9945", RUN+="/bin/su adrien -c '/usr/bin/gnome-screensaver-command -d'"
ACTION=="remove", ENV{ID_FS_UUID}=="E040-9945", RUN+="/bin/su adrien -c '/usr/bin/gnome-screensaver-command -l'"
```
Without success :-s.

My first question is : What am I doing wrong? (I test the commands above as root and it worked :-s.
And my second question is : Is there a better way to do this? (I'd like not to use a daemon or a non system tool)

Thank you for any help you'd bring.

Little Nooby

[SOLUTION]
I found out the solution thanks to a friend of mine : 
ACTION=="add", ENV{ID_FS_UUID}=="E040-9945", RUN+="/bin/su adrien -c 'export DISPLAY=:0 && /usr/bin/gnome-screensaver-command -d'"
ACTION=="remove", ENV{ID_FS_UUID}=="E040-9945", RUN+="/bin/su adrien -c 'export DISPLAY=:0 && /usr/bin/gnome-screensaver-command -l'"

:0 is the result from $ echo $DISPLAY #inside a terminal

---

