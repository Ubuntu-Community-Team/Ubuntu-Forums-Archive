---
title: "I can't get cron to work"
date: 2008-04-21
forum: General Help
---

### Post by elmer_42 on 2008-04-21
I have looked at [many]("http://ubuntuforums.org/showthread.php?t=5281") [threads]("http://ubuntuforums.org/showthread.php?t=190617") [regarding]("http://ubuntuforums.org/showthread.php?t=401703") [cron]("http://ubuntuforums.org/showthread.php?t=519631"), and I can't get cron to work. The one job that is there does not run at 6:22, or whatever time I set it to. Without further ado, here is the output of some commands that were asked in those topics:
```
staylor@Mariner:~$ sudo crontab -e
crontab: installing new crontab
staylor@Mariner:~$ sudo crontab -l
22 6 * * * /home/staylor/Alarm.sh
staylor@Mariner:~$ sudo cat /etc/cron.allow
staylor
root
staylor@Mariner:~$ cat Alarm.sh
#! /bin/sh
export XAUTHORITY="/home/user/.Xauthority"
export DISPLAY=:0.0
totem ~/Music/alarm.mp3
staylor@Mariner:~$ sudo cat /var/log/syslog
*a whole lot of stuff*
Apr 21 06:21:17 Mariner crontab[7577]: (root) BEGIN EDIT (root)
Apr 21 06:21:27 Mariner crontab[7577]: (root) REPLACE (root)
Apr 21 06:21:27 Mariner crontab[7577]: (root) END EDIT (root)
Apr 21 06:21:37 Mariner crontab[7602]: (root) BEGIN EDIT (root)
Apr 21 06:21:39 Mariner crontab[7602]: (root) END EDIT (root)
Apr 21 06:22:01 Mariner /usr/sbin/cron[5385]: (root) RELOAD (crontabs/root)
Apr 21 06:22:01 Mariner /USR/SBIN/CRON[7606]: (root) CMD (/home/staylor/Alarm.sh)
```

---

### Post by Thanoulis on 2008-04-21
The crontab job you're trying to do is about root...did you try to manage your crontab as user?
```
crontab -e
```(i mean without the *sudo*)

---

### Post by justleen on 2008-04-21
is the Alarm.sh executable?

what if you do something "simple" in your cron?
like:
```
22 6 * * * logger "this is a test" 
```

this should add a line "this is a test" to your messages logfile.

---

### Post by elmer_42 on 2008-04-23
I can access it without sudo, but it still doesn't work.
Yes, when I run ./Alarm.sh or sh Alarm.sh, it opens up Totem and plays the song I have saved as Alarm.mp3. I had to change the file though, I kept getting errors. Now it has no XAUTHORITY or DISPLAY.
I added this line when I typed sudo crontab -e
```
29 7 * * * logger "lorem ipsum dolor sit amet"
```
and this is my log:
```
Apr 23 07:29:01 Mariner /usr/sbin/cron[5385]: (root) RELOAD (crontabs/root)
Apr 23 07:29:01 Mariner /USR/SBIN/CRON[26254]: (root) CMD (logger "lorem ipsum dolor sit amet")
Apr 23 07:29:01 Mariner logger: lorem ipsum dolor sit amet
```

---

### Post by elmer_42 on 2008-04-23
So does anybody know what is wrong? I really hate having to change to Windows every night to run my alarm clock.

---

