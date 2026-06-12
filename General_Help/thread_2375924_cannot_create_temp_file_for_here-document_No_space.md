---
title: "cannot create temp file for here-document: No space left on device"
date: 2017-10-28
forum: General Help
---

### Post by abc617 on 2017-10-28
Hi,

I'm more of a beginner when it comes to Ubuntu, so forgive me for any stupid questions.

Anyways, a couple of weeks ago, I upgraded my personal home Ubuntu server from 14.04 --> 16.04 because I noticed the server was getting slow and unresponsive and didn't know what was causing it. 

During the initial set up I let the default Ubuntu 16.04 set up the partitions and set the sizes/allocations of disk space, and once the initial set up was and re-added all my drives, set up Samba, and moved some large files across some of my hard drives.


But now when type a command and hit "Tab' to auto-complete the command, I get the following error

> -bash: cannot create temp file for here-document: No space left on device

I checked to see what disk or partition could be full:

```
ricky@flynt:~$ df
Filesystem                  1K-blocks       Used  Available Use% Mounted on
udev                          3892124          0    3892124   0% /dev
tmpfs                          782460       9264     773196   2% /run
/dev/mapper/flynt--vg-root   49156404   46671652          0 100% /
tmpfs                         3912288          4    3912284   1% /dev/shm
tmpfs                            5120          4       5116   1% /run/lock
tmpfs                         3912288          0    3912288   0% /sys/fs/cgroup
/dev/sdb                   1922729864  134337500 1690700252   8% /media/2TB
/dev/sda1                      482922     157200     300788  35% /boot
/dev/sdc1                  2113655724 1809132080  197133132  91% /media/3TB
tmpfs                          782460          0     782460   0% /run/user/1000

```

So I can see that the /dev/mapper/flynt--vg-root partition is full and when I check Webmin, I have the following error message:

[IMG]https://i.imgur.com/QQQSYb3.png[/IMG]


Since I'm a newbie, I don't know what I should do to try to clear that /dev/mapper.. partition or free up that 46.88GB file system.

---

### Post by ian-weisser on 2017-10-28
Well, what's on there that's taking up so much space?
If you have a Desktop Environment, look for the 'Disk Usage Analyzer' application

---

### Post by drs305 on 2017-10-28
I wrote this about 8 years ago about how to analyze and recover lost disk space. I think it still applies:
[https://ubuntuforums.org/showthread.php?t=1122670]("https://ubuntuforums.org/showthread.php?t=1122670")

---

### Post by abc617 on 2017-10-29
> **ian-weisser said:**
> Well, what's on there that's taking up so much space?
If you have a Desktop Environment, look for the 'Disk Usage Analyzer' application
Unfortunately my Ubuntu server is "headless" so all I have is the CLI, so all I know right now is using "du" and "df" to analyze my disk usage right now.




> **drs305 said:**
> I wrote this about 8 years ago about how to analyze and recover lost disk space. I think it still applies:
[https://ubuntuforums.org/showthread.php?t=1122670](https://ubuntuforums.org/showthread.php?t=1122670)
I was able to follow some steps in clearing some space. And now I'm able to use "Tab" to auto-complete some commands now, which is what I wanted.

However this whole escape has me worried with the fact that my root directory "/" is still near 100% and I looked through everything in your guide and I'm still not able to figure out how to free up that 46GB of space.

---

### Post by ian-weisser on 2017-10-29
> **abc617 said:**
> all I have is the CLI, so all I know right now is using "du" and "df" to analyze my disk usage right now.

du is all you need. This command will list the largest files and directories at the bottom:
```
$ du -a / | sort -n
```

Show us the biggest 10 or 15.

---

### Post by abc617 on 2017-10-29
> **ian-weisser said:**
> du is all you need. This command will list the largest files and directories at the bottom:
```
$ du -a / | sort -n
```

Show us the biggest 10 or 15.

Thanks for your help. I was able to find what was eating up all my space doing some more digging. I found that in the "/var/log" directory, my "syslog" file were eating up all my available space ( 30G for the syslog file ).

I found the following the instructions which helped out: [https://askubuntu.com/questions/746535/var-log-syslog-growing-indefinitely-in-size](https://askubuntu.com/questions/746535/var-log-syslog-growing-indefinitely-in-size) and [https://askubuntu.com/questions/746535/var-log-syslog-growing-indefinitely-in-size](https://askubuntu.com/questions/746535/var-log-syslog-growing-indefinitely-in-size)

I checked out the syslog file and I didn't find strange entries, but I didn't look too in depth because it was thousands of lines long. Anyways i just followed the instructions in the links above and I fixed it by just writing null to the syslog files 

```
sudo su
> /var/log/syslog
```

After rebooting, I my syslog file shrank from 30G to 707M. That's still a large log file, but it cleaned up a lot of the space in my root directory.

---

### Post by drs305 on 2017-10-29
That is still a large file if you just deleted it. Keep an eye on it - at some point you are probably going to have to open it up and find out where the problem is. If you find a recurring error/entry you can post it on these forums and we can help you troubleshoot it.

---

### Post by efflandt on 2017-10-29
Normally a cron job automatically rotates logs, compresses older ones, and beyond a certain point deletes them. Either check your syslog to see what is growing it, or maybe why /etc/cron.daily/logrotate is not running daily like it should.

I just noticed that my logs are being loaded up with compiz for some reason regularly reporting my refresh rate, udisksd not ignoring (repeatedly reporting) an unmounted drive intentionally in standby when doing its smart check, and something that appears to be from Steam or a Steam game that should not even be in syslog (Steam normally logs to files in /tmp).```
~$ ls -l /var/log/syslog*
-rw-r----- 1 syslog adm  30368 Oct 29 11:02 /var/log/syslog
-rw-r----- 1 syslog adm 176746 Oct 29 07:35 /var/log/syslog.1
-rw-r----- 1 syslog adm   9332 Oct 28 07:35 /var/log/syslog.2.gz
-rw-r----- 1 syslog adm  11140 Oct 27 07:35 /var/log/syslog.3.gz
-rw-r----- 1 syslog adm  42358 Oct 26 07:35 /var/log/syslog.4.gz
-rw-r----- 1 syslog adm  15241 Oct 25 07:35 /var/log/syslog.5.gz
-rw-r----- 1 syslog adm   9114 Oct 24 07:35 /var/log/syslog.6.gz
-rw-r----- 1 syslog adm   7777 Oct 23 07:35 /var/log/syslog.7.gz
```

---

