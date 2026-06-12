---
title: "Cannot make rTorrent run on System Startup"
date: 2007-05-24
forum: General Help
---

### Post by tomcheng76 on 2007-05-24
Hi guys
I follow this how-to [here]("http://libtorrent.rakshasa.no/wiki/RTorrentCommonTasks")

i run the script [here]("http://libtorrent.rakshasa.no/attachment/wiki/RTorrentCommonTasks/rtorrentInit.sh?format=raw") successfully by
```

$ su
Password: 
root@ubuntu:/etc/init.d# ./rtorrent start
Starting rtorrent: rtorrent.

```
however,it just don't run on system startup :(
i suspect the "su -c" cause this problem

if i use

$ sudo ./rtorrent start

the error is 

./rtorrent: 39: Syntax error: "(" unexpected

my default run level is 2
and my OS is Ubuntu feisty

Thanks in advance

---

### Post by fanatik on 2007-05-24
just having a script in /etc/init.d isn't enough. you need to create links in your runlevel directory back to the script in init.d. the runlevel directory for runlevel 2 is /etc/rc2.d, if you do ls -l /etc/rc2.d you will see what I mean. now you can create the links manually, but it's easier to use update-rc.d, like this:

```
$ sudo update-rc.d rtorrent start 20 2
```
or
```
$ sudo update-rc.d rtorrent defaults
```

use man update-rc.d for full info.

HTH

---

### Post by tomcheng76 on 2007-05-24
thanks for the quick reply
i have already run the code

$ sudo update-rc.d rtorrent defaults

which is included in the how-to
and i can confirm that there is a symlink inside rc2.d where it is S20rtorrent which means start the script

the problem is that i have really no idea why it doesnt start
i check that by issuing this command

$ ps aux | grep rtorrent

i got nothing

if i start the script manually, i got

$ ps aux | grep rtorrent
username    9979  0.0  0.2   3904  1120 ?        Ss   00:20   0:00 SCREEN -dm -S rtorrent
username   10251  0.1  0.6   8880  3304 pts/2    Ss+  01:19   0:00 rtorrent -n -o import=/home/bomber/.bgrtorrent.rc
root     10255  0.0  0.1   2740   772 pts/0    R+   01:19   0:00 grep rtorrent

Can someone tell me how to check the boot up log, what is the log path :(

---

### Post by tomcheng76 on 2007-05-25
bump

---

### Post by tomcheng76 on 2007-05-25
bump, anyone plz help

---

### Post by tomcheng76 on 2007-05-25
fixed the problem
it is because default sh for Ubuntu is dash
dash cant use
"test=("a" "b")"
after changing the script
from
!#/bin/sh
to
!#/bin/bash
it works
[here]("http://libtorrent.rakshasa.no/ticket/902") is the soln.

---

