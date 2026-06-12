---
title: "Is Cron running?"
date: 2013-04-07
forum: General Help
---

### Post by GameX2 on 2013-04-07
Hi,


This is my first time trying to run a Cron job (Rsync).  My /etc/crontab look like this:

```
# /etc/crontab: system-wide crontab
# Unlike any other crontab you don't have to run the `crontab'
# command to install the new version when you edit this file
# and files in /etc/cron.d. These files also have username fields,
# that none of the other crontabs do.

SHELL=/bin/sh
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin

# m h dom mon dow user    command
17 *    * * *    root    cd / && run-parts --report /etc/cron.hourly
25 6    * * *    root    test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.daily )
47 6    * * 7    root    test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.weekly )
52 6    1 * *    root    test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.monthly )
 * *    * * *   root    notify-send 'Crontab Test!'
#


```

On the line " * *    * * *   root    notify-send 'Crontab Test!' ", I've also tried to launch a Shell Script from my home directory.  The script is working, but does not execute every minute, like it should.

Here's the output of: ls -lut /etc/init.d/cron

```
lrwxrwxrwx 1 root root 21 avr  7 11:44 /etc/init.d/cron -> /lib/init/upstart-job
```
Does this mean Cron was executed for the last time on.. April 21th 2012 ??

When I type " /etc/init.d/cron restart ", I get this:

Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service cron restart

```
Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the stop(8) and then start(8) utilities,
e.g. stop cron ; start cron. The restart(8) utility is also available.
stop: Rejected send message, 1 matched rules; type="method_call", sender=":1.589" (uid=1000 pid=32666 comm="stop cron ") interface="com.ubuntu.Upstart0_6.Job" member="Stop" error name="(unset)" requested_reply="0" destination="com.ubuntu.Upstart" (uid=0 pid=1 comm="/sbin/init")
```

And when I type " service cron start ", here's the output:

```
start: Rejected send message, 1 matched rules; type="method_call", sender=":1.590" (uid=1000 pid=2191 comm="start cron ") interface="com.ubuntu.Upstart0_6.Job" member="Start" error name="(unset)" requested_reply="0" destination="com.ubuntu.Upstart" (uid=0 pid=1 comm="/sbin/init")
```

I don't understand what's happening. :confused:

Thanks for the help!

---

### Post by SeijiSensei on 2013-04-07
Type the command "ps aux | grep cron"?  Do you see an entry like:

```
root      1213  0.0  0.0   2620   604 ?        Ss   Mar23   0:03 cron
```

If so, cron is running.

---

### Post by GameX2 on 2013-04-07
Yes.

```
root      1347  0.0  0.0  19112  1028 ?        Ss   Apr06   0:00 cron
gamex      5122  0.0  0.0   9364   920 pts/0    S+   14:43   0:00 grep --color=auto cron
```

Can you tell me what is wrong with my Cron file (the last line) ?


```
# /etc/crontab: system-wide crontab
# Unlike any other crontab you don't have to run the `crontab'
# command to install the new version when you edit this file
# and files in /etc/cron.d. These files also have username fields,
# that none of the other crontabs do.

SHELL=/bin/sh
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin

# m h dom mon dow user    command
17 *    * * *    root    cd / && run-parts --report /etc/cron.hourly
25 6    * * *    root    test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.daily )
47 6    * * 7    root    test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.weekly )
52 6    1 * *    root    test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.monthly )
 * *    * * *   root    notify-send 'Crontab Test!'
#


```

Sorry for the basic question - thanks for the reply!

---

### Post by SeijiSensei on 2013-04-07
I don't have a "notify-send" command on my machine running Kubuntu.  Did you try running that command from the command prompt with "sudo notify-send 'Hello'"?

Cron results are logged in /var/log/syslog.  Use "sudo grep cron /var/log/syslog" to see them.

---

### Post by GameX2 on 2013-04-07
The "notify-send" command is used to send basic notifications easily; you first have to install the package " libnotify-bin ":
[http://www.cyberciti.biz/tips/spice-up-your-unix-linux-shell-scripts.html](http://www.cyberciti.biz/tips/spice-up-your-unix-linux-shell-scripts.html)
In my case, sudo notify-send 'Hello' is working (It does not require root).

Here's the output of sudo grep cron /var/log/syslog :

```
Apr  7 07:39:51 Portable-Ubuntu anacron[19490]: Job `cron.daily' terminated (mailing output)
Apr  7 07:39:51 Portable-Ubuntu anacron[19490]: Can't find sendmail at /usr/sbin/sendmail, not mailing output
Apr  7 07:39:51 Portable-Ubuntu anacron[19490]: Normal exit (1 job run)
Apr  7 08:17:01 Portable-Ubuntu CRON[29292]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Apr  7 09:17:01 Portable-Ubuntu CRON[25446]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Apr  7 10:17:01 Portable-Ubuntu CRON[20540]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Apr  7 11:17:01 Portable-Ubuntu CRON[6857]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Apr  7 11:44:48 Portable-Ubuntu crontab[895]: (gamex) LIST (gamex)
Apr  7 11:47:26 Portable-Ubuntu crontab[6420]: (gamex) BEGIN EDIT (gamex)
Apr  7 11:47:29 Portable-Ubuntu crontab[6420]: (gamex) END EDIT (gamex)
Apr  7 11:56:01 Portable-Ubuntu cron[1347]: (*system*) RELOAD (/etc/crontab)
Apr  7 11:58:01 Portable-Ubuntu cron[1347]: (*system*) RELOAD (/etc/crontab)
Apr  7 11:59:01 Portable-Ubuntu cron[1347]: (*system*) RELOAD (/etc/crontab)
Apr  7 12:00:57 Portable-Ubuntu cron[32415]: (CRON) DEATH (can't open or create /var/run/crond.pid: Permission denied)
Apr  7 12:01:05 Portable-Ubuntu cron[32517]: (CRON) DEATH (can't lock /var/run/crond.pid, otherpid may be 1347: Resource temporarily unavailable)
Apr  7 12:05:01 Portable-Ubuntu cron[1347]: (*system*) RELOAD (/etc/crontab)
Apr  7 12:08:52 Portable-Ubuntu /usr/bin/crontab[16435]: (gamex) LIST (gamex)
Apr  7 12:09:01 Portable-Ubuntu /usr/bin/crontab[16569]: (gamex) LIST (gamex)
Apr  7 12:09:09 Portable-Ubuntu /usr/bin/crontab[16675]: (gamex) REPLACE (gamex)
Apr  7 12:09:09 Portable-Ubuntu /usr/bin/crontab[16677]: (gamex) LIST (gamex)
Apr  7 12:09:10 Portable-Ubuntu /usr/bin/crontab[16693]: (gamex) LIST (gamex)
Apr  7 12:09:19 Portable-Ubuntu /usr/bin/crontab[17159]: (gamex) LIST (gamex)
Apr  7 12:09:28 Portable-Ubuntu /usr/bin/crontab[17288]: (gamex) LIST (gamex)
Apr  7 12:09:37 Portable-Ubuntu /usr/bin/crontab[17783]: (gamex) LIST (gamex)
Apr  7 12:09:46 Portable-Ubuntu /usr/bin/crontab[17902]: (gamex) LIST (gamex)
Apr  7 12:09:55 Portable-Ubuntu /usr/bin/crontab[18410]: (gamex) LIST (gamex)
Apr  7 12:10:01 Portable-Ubuntu cron[1347]: (gamex) RELOAD (crontabs/gamex)
Apr  7 12:10:04 Portable-Ubuntu /usr/bin/crontab[18525]: (gamex) LIST (gamex)
Apr  7 12:10:13 Portable-Ubuntu /usr/bin/crontab[19045]: (gamex) LIST (gamex)
Apr  7 12:10:22 Portable-Ubuntu /usr/bin/crontab[19160]: (gamex) LIST (gamex)
Apr  7 12:10:31 Portable-Ubuntu /usr/bin/crontab[19278]: (gamex) LIST (gamex)
Apr  7 12:10:40 Portable-Ubuntu /usr/bin/crontab[19795]: (gamex) LIST (gamex)
Apr  7 12:10:49 Portable-Ubuntu /usr/bin/crontab[19916]: (gamex) LIST (gamex)
Apr  7 12:10:58 Portable-Ubuntu /usr/bin/crontab[20424]: (gamex) LIST (gamex)
Apr  7 12:11:07 Portable-Ubuntu /usr/bin/crontab[20542]: (gamex) LIST (gamex)
Apr  7 12:11:16 Portable-Ubuntu /usr/bin/crontab[21050]: (gamex) LIST (gamex)
Apr  7 12:11:25 Portable-Ubuntu /usr/bin/crontab[21168]: (gamex) LIST (gamex)
Apr  7 12:11:34 Portable-Ubuntu /usr/bin/crontab[21688]: (gamex) LIST (gamex)
Apr  7 12:11:43 Portable-Ubuntu /usr/bin/crontab[21795]: (gamex) LIST (gamex)
Apr  7 12:11:52 Portable-Ubuntu /usr/bin/crontab[22323]: (gamex) LIST (gamex)
Apr  7 12:12:01 Portable-Ubuntu /usr/bin/crontab[22441]: (gamex) LIST (gamex)
Apr  7 12:12:10 Portable-Ubuntu /usr/bin/crontab[22558]: (gamex) LIST (gamex)
Apr  7 12:12:19 Portable-Ubuntu /usr/bin/crontab[23085]: (gamex) LIST (gamex)
Apr  7 12:12:28 Portable-Ubuntu /usr/bin/crontab[23200]: (gamex) LIST (gamex)
Apr  7 12:12:37 Portable-Ubuntu /usr/bin/crontab[23716]: (gamex) LIST (gamex)
Apr  7 12:12:46 Portable-Ubuntu /usr/bin/crontab[23831]: (gamex) LIST (gamex)
Apr  7 12:12:55 Portable-Ubuntu /usr/bin/crontab[24365]: (gamex) LIST (gamex)
Apr  7 12:13:04 Portable-Ubuntu /usr/bin/crontab[24481]: (gamex) LIST (gamex)
Apr  7 12:13:13 Portable-Ubuntu /usr/bin/crontab[25010]: (gamex) LIST (gamex)
Apr  7 12:13:22 Portable-Ubuntu /usr/bin/crontab[25114]: (gamex) LIST (gamex)
Apr  7 12:13:24 Portable-Ubuntu /usr/bin/crontab[25143]: (gamex) REPLACE (gamex)
Apr  7 12:13:24 Portable-Ubuntu /usr/bin/crontab[25145]: (gamex) LIST (gamex)
Apr  7 12:13:31 Portable-Ubuntu /usr/bin/crontab[25243]: (gamex) LIST (gamex)
Apr  7 12:13:40 Portable-Ubuntu /usr/bin/crontab[25831]: (gamex) LIST (gamex)
Apr  7 12:13:49 Portable-Ubuntu /usr/bin/crontab[25955]: (gamex) LIST (gamex)
Apr  7 12:13:58 Portable-Ubuntu /usr/bin/crontab[26443]: (gamex) LIST (gamex)
Apr  7 12:14:01 Portable-Ubuntu cron[1347]: (gamex) RELOAD (crontabs/gamex)
Apr  7 12:14:07 Portable-Ubuntu /usr/bin/crontab[26565]: (gamex) LIST (gamex)
Apr  7 12:14:16 Portable-Ubuntu /usr/bin/crontab[27036]: (gamex) LIST (gamex)
Apr  7 12:14:25 Portable-Ubuntu /usr/bin/crontab[27165]: (gamex) LIST (gamex)
Apr  7 12:14:34 Portable-Ubuntu /usr/bin/crontab[27661]: (gamex) LIST (gamex)
Apr  7 12:14:43 Portable-Ubuntu /usr/bin/crontab[27835]: (gamex) LIST (gamex)
Apr  7 12:14:52 Portable-Ubuntu /usr/bin/crontab[28337]: (gamex) LIST (gamex)
Apr  7 12:15:01 Portable-Ubuntu cron[1347]: (*system*) RELOAD (/etc/crontab)
Apr  7 12:15:01 Portable-Ubuntu /usr/bin/crontab[28487]: (gamex) LIST (gamex)
Apr  7 12:15:10 Portable-Ubuntu /usr/bin/crontab[28609]: (gamex) LIST (gamex)
Apr  7 12:15:19 Portable-Ubuntu /usr/bin/crontab[29153]: (gamex) LIST (gamex)
Apr  7 12:15:28 Portable-Ubuntu /usr/bin/crontab[29271]: (gamex) LIST (gamex)
Apr  7 12:15:37 Portable-Ubuntu /usr/bin/crontab[29780]: (gamex) LIST (gamex)
Apr  7 12:15:46 Portable-Ubuntu /usr/bin/crontab[29909]: (gamex) LIST (gamex)
Apr  7 12:15:55 Portable-Ubuntu /usr/bin/crontab[30423]: (gamex) LIST (gamex)
Apr  7 12:16:04 Portable-Ubuntu /usr/bin/crontab[30628]: (gamex) LIST (gamex)
Apr  7 12:16:13 Portable-Ubuntu /usr/bin/crontab[31135]: (gamex) LIST (gamex)
Apr  7 12:16:22 Portable-Ubuntu /usr/bin/crontab[31239]: (gamex) LIST (gamex)
Apr  7 12:16:31 Portable-Ubuntu /usr/bin/crontab[31522]: (gamex) LIST (gamex)
Apr  7 12:16:40 Portable-Ubuntu /usr/bin/crontab[31888]: (gamex) LIST (gamex)
Apr  7 12:16:49 Portable-Ubuntu /usr/bin/crontab[32006]: (gamex) LIST (gamex)
Apr  7 12:16:58 Portable-Ubuntu /usr/bin/crontab[32501]: (gamex) LIST (gamex)
Apr  7 12:17:01 Portable-Ubuntu CRON[32545]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Apr  7 12:17:07 Portable-Ubuntu /usr/bin/crontab[32634]: (gamex) LIST (gamex)
Apr  7 12:17:16 Portable-Ubuntu /usr/bin/crontab[679]: (gamex) LIST (gamex)
Apr  7 12:17:25 Portable-Ubuntu /usr/bin/crontab[844]: (gamex) LIST (gamex)
Apr  7 12:17:34 Portable-Ubuntu /usr/bin/crontab[1494]: (gamex) LIST (gamex)
Apr  7 12:17:43 Portable-Ubuntu /usr/bin/crontab[1630]: (gamex) LIST (gamex)
Apr  7 12:17:52 Portable-Ubuntu /usr/bin/crontab[2248]: (gamex) LIST (gamex)
Apr  7 12:18:01 Portable-Ubuntu /usr/bin/crontab[2441]: (gamex) LIST (gamex)
Apr  7 12:18:10 Portable-Ubuntu /usr/bin/crontab[2570]: (gamex) LIST (gamex)
Apr  7 12:18:19 Portable-Ubuntu /usr/bin/crontab[3090]: (gamex) LIST (gamex)
Apr  7 12:18:28 Portable-Ubuntu /usr/bin/crontab[3205]: (gamex) LIST (gamex)
Apr  7 12:18:33 Portable-Ubuntu /usr/bin/crontab[3688]: (gamex) REPLACE (gamex)
Apr  7 12:18:33 Portable-Ubuntu /usr/bin/crontab[3690]: (gamex) LIST (gamex)
Apr  7 12:18:37 Portable-Ubuntu /usr/bin/crontab[3746]: (gamex) LIST (gamex)
Apr  7 12:18:46 Portable-Ubuntu /usr/bin/crontab[3862]: (gamex) LIST (gamex)
Apr  7 12:18:55 Portable-Ubuntu /usr/bin/crontab[4396]: (gamex) LIST (gamex)
Apr  7 12:19:01 Portable-Ubuntu cron[1347]: (*system*) RELOAD (/etc/crontab)
Apr  7 12:19:01 Portable-Ubuntu cron[1347]: (gamex) RELOAD (crontabs/gamex)
Apr  7 12:19:04 Portable-Ubuntu /usr/bin/crontab[4612]: (gamex) LIST (gamex)
Apr  7 12:19:13 Portable-Ubuntu /usr/bin/crontab[5136]: (gamex) LIST (gamex)
Apr  7 12:19:22 Portable-Ubuntu /usr/bin/crontab[5251]: (gamex) LIST (gamex)
Apr  7 12:19:31 Portable-Ubuntu /usr/bin/crontab[5372]: (gamex) LIST (gamex)
Apr  7 12:19:40 Portable-Ubuntu /usr/bin/crontab[5878]: (gamex) LIST (gamex)
15:06:24
Apr  7 12:19:58 Portable-Ubuntu /usr/bin/crontab[6541]: (gamex) LIST (gamex)
Apr  7 12:20:06 Portable-Ubuntu /usr/bin/crontab[6682]: (gamex) LIST (gamex)
Apr  7 12:20:07 Portable-Ubuntu /usr/bin/crontab[6701]: (gamex) LIST (gamex)
Apr  7 12:20:14 Portable-Ubuntu /usr/bin/crontab[7204]: (gamex) REPLACE (gamex)
Apr  7 12:20:14 Portable-Ubuntu /usr/bin/crontab[7206]: (gamex) LIST (gamex)
Apr  7 12:21:01 Portable-Ubuntu cron[1347]: (gamex) RELOAD (crontabs/gamex)
Apr  7 12:28:01 Portable-Ubuntu cron[1347]: (*system*) RELOAD (/etc/crontab)
Apr  7 12:35:01 Portable-Ubuntu cron[1347]: (*system*) RELOAD (/etc/crontab)
Apr  7 12:36:01 Portable-Ubuntu cron[1347]: (*system*) RELOAD (/etc/crontab)
Apr  7 13:17:01 Portable-Ubuntu CRON[23925]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Apr  7 13:45:26 Portable-Ubuntu anacron[17046]: Anacron 2.3 started on 2013-04-07
Apr  7 13:45:26 Portable-Ubuntu anacron[17046]: Normal exit (0 jobs run)
Apr  7 13:45:36 Portable-Ubuntu anacron[17577]: Anacron 2.3 started on 2013-04-07
Apr  7 13:45:36 Portable-Ubuntu anacron[17577]: Normal exit (0 jobs run)
Apr  7 13:45:36 Portable-Ubuntu anacron[17736]: Anacron 2.3 started on 2013-04-07
Apr  7 13:45:36 Portable-Ubuntu anacron[17736]: Normal exit (0 jobs run)
Apr  7 14:17:01 Portable-Ubuntu CRON[23869]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
```

---

### Post by CaptainMark on 2013-04-07
Trying to run graphical applications from cron often gives problems, you're not the only one wanting some visual feedback from a cron job though, see here [http://ubuntuforums.org/showthread.php?t=1727148](http://ubuntuforums.org/showthread.php?t=1727148)

---

### Post by rnerwein on 2013-04-07
hi
my first question is - why you aint't using "crontab -e" under your user-account.
but to run application using a desktop you can write a script with the following contens:
DISPLAY=:0.0
export DISPLAY
/usr/bin/notify-send "hello world"
exit 0

# important are the two lines with DISPLAY
and your crontab file can look like this:
*/2 * * * * /home/richi/tmp/notify_me

the script must be executeable: -rwxr-xr-x 
ciao

---

### Post by jawilljr on 2013-04-07
The following works for me:

```
* * * * * DISPLAY=:0.0 XAUTHORITY=~/.Xauthority notify-send "Hello World"
```

I got it [from here.](http://www.commandlinefu.com/commands/view/6228/better-way-to-use-notify-send-with-at-or-cron)

Jerry

---

### Post by Dave_L on 2013-04-07
Another way of testing cron:

```
* * * * * root date >>/tmp/date.log 2>&1
```

---

