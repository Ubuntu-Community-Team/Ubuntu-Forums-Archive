---
title: "[SOLVED] Prevent cron from logging to syslog"
date: 2008-07-02
forum: General Help
---

### Post by akudewan on 2008-07-02
I have made a little script that executes every 10 minutes as a cron job. The problem is that it clutters my /var/log/syslog file.

Any way I can make it NOT log to syslog ?

```

Jul  2 08:08:34 ranjandesk syslogd 1.5.0#1ubuntu1: restart.
Jul  2 08:08:34 ranjandesk anacron[25457]: Job `cron.daily' terminated
Jul  2 08:08:34 ranjandesk anacron[25457]: Job `cron.monthly' started
Jul  2 08:08:34 ranjandesk anacron[754]: Updated timestamp for job `cron.monthly' to 2008-07-02
Jul  2 08:10:02 ranjandesk /USR/SBIN/CRON[6411]: (akudewan) CMD (/usr/local/bin/keeponline.sh 1> /dev/null)
Jul  2 08:10:56 ranjandesk anacron[25457]: Job `cron.monthly' terminated
Jul  2 08:10:56 ranjandesk anacron[25457]: Normal exit (2 jobs run)
Jul  2 08:17:01 ranjandesk /USR/SBIN/CRON[9807]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jul  2 08:20:01 ranjandesk /USR/SBIN/CRON[9879]: (akudewan) CMD (/usr/local/bin/keeponline.sh 1> /dev/null)
Jul  2 08:30:01 ranjandesk /USR/SBIN/CRON[10108]: (akudewan) CMD (/usr/local/bin/keeponline.sh 1> /dev/null)
Jul  2 08:40:01 ranjandesk /USR/SBIN/CRON[10398]: (akudewan) CMD (/usr/local/bin/keeponline.sh 1> /dev/null)
Jul  2 08:50:01 ranjandesk /USR/SBIN/CRON[10693]: (akudewan) CMD (/usr/local/bin/keeponline.sh 1> /dev/null)
Jul  2 09:00:01 ranjandesk /USR/SBIN/CRON[10936]: (akudewan) CMD (/usr/local/bin/keeponline.sh 1> /dev/null)
Jul  2 09:10:01 ranjandesk /USR/SBIN/CRON[11200]: (akudewan) CMD (/usr/local/bin/keeponline.sh 1> /dev/null)
Jul  2 09:17:01 ranjandesk /USR/SBIN/CRON[11427]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jul  2 09:20:01 ranjandesk /USR/SBIN/CRON[11503]: (akudewan) CMD (/usr/local/bin/keeponline.sh 1> /dev/null)
Jul  2 09:30:01 ranjandesk /USR/SBIN/CRON[11749]: (akudewan) CMD (/usr/local/bin/keeponline.sh 1> /dev/null)
Jul  2 09:40:01 ranjandesk /USR/SBIN/CRON[12033]: (akudewan) CMD (/usr/local/bin/keeponline.sh 1> /dev/null)
Jul  2 09:50:01 ranjandesk /USR/SBIN/CRON[12338]: (akudewan) CMD (/usr/local/bin/keeponline.sh 1> /dev/null)
Jul  2 10:00:01 ranjandesk /USR/SBIN/CRON[12589]: (akudewan) CMD (/usr/local/bin/keeponline.sh 1> /dev/null)
Jul  2 10:10:01 ranjandesk /USR/SBIN/CRON[12837]: (akudewan) CMD (/usr/local/bin/keeponline.sh 1> /dev/null)
Jul  2 10:17:01 ranjandesk /USR/SBIN/CRON[13087]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jul  2 10:20:01 ranjandesk /USR/SBIN/CRON[13163]: (akudewan) CMD (/usr/local/bin/keeponline.sh 1> /dev/null)
Jul  2 10:30:02 ranjandesk /USR/SBIN/CRON[13410]: (akudewan) CMD (/usr/local/bin/keeponline.sh 1> /dev/null)
Jul  2 10:40:01 ranjandesk /USR/SBIN/CRON[13650]: (akudewan) CMD (/usr/local/bin/keeponline.sh 1> /dev/null)
Jul  2 10:50:01 ranjandesk /USR/SBIN/CRON[14019]: (akudewan) CMD (/usr/local/bin/keeponline.sh 1> /dev/null)
Jul  2 11:00:01 ranjandesk /USR/SBIN/CRON[14272]: (akudewan) CMD (/usr/local/bin/keeponline.sh 1> /dev/null)
Jul  2 11:10:01 ranjandesk /USR/SBIN/CRON[14694]: (akudewan) CMD (/usr/local/bin/keeponline.sh 1> /dev/null)
Jul  2 11:17:01 ranjandesk /USR/SBIN/CRON[14893]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jul  2 11:20:01 ranjandesk /USR/SBIN/CRON[14953]: (akudewan) CMD (/usr/local/bin/keeponline.sh 1> /dev/null)
Jul  2 11:30:01 ranjandesk /USR/SBIN/CRON[15123]: (akudewan) CMD (/usr/local/bin/keeponline.sh 1> /dev/null)
Jul  2 11:40:01 ranjandesk /USR/SBIN/CRON[15287]: (akudewan) CMD (/usr/local/bin/keeponline.sh 1> /dev/null)
Jul  2 11:45:56 ranjandesk init: tty1 main process ended, respawning
Jul  2 11:50:01 ranjandesk /USR/SBIN/CRON[15637]: (akudewan) CMD (/usr/local/bin/keeponline.sh 1> /dev/null)

```

---

### Post by dcstar on 2008-07-02
> **akudewan said:**
> I have made a little script that executes every 10 minutes as a cron job. The problem is that it clutters my /var/log/syslog file.

Any way I can make it NOT log to syslog ?


Try making the cron job output "2> /dev/null"

---

### Post by akudewan on 2008-07-02
Hi,

Thanks for the reply. I did what you said, but I'm still getting the entries in syslog.

```

Jul  2 12:10:06 ranjandesk crontab[16095]: (akudewan) BEGIN EDIT (akudewan)
Jul  2 12:10:17 ranjandesk crontab[16095]: (akudewan) REPLACE (akudewan)
Jul  2 12:10:17 ranjandesk crontab[16095]: (akudewan) END EDIT (akudewan)
Jul  2 12:11:01 ranjandesk /usr/sbin/cron[6459]: (akudewan) RELOAD (crontabs/akudewan)
Jul  2 12:17:01 ranjandesk /USR/SBIN/CRON[16275]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jul  2 12:20:01 ranjandesk /USR/SBIN/CRON[16352]: (akudewan) CMD (/usr/local/bin/keeponline.sh 1> /dev/null 2> /dev/null)
Jul  2 12:30:01 ranjandesk /USR/SBIN/CRON[16748]: (akudewan) CMD (/usr/local/bin/keeponline.sh 1> /dev/null 2> /dev/null)
Jul  2 12:40:01 ranjandesk /USR/SBIN/CRON[16972]: (akudewan) CMD (/usr/local/bin/keeponline.sh 1> /dev/null 2> /dev/null)
Jul  2 12:50:01 ranjandesk /USR/SBIN/CRON[17279]: (akudewan) CMD (/usr/local/bin/keeponline.sh 1> /dev/null 2> /dev/null)
Jul  2 13:00:01 ranjandesk /USR/SBIN/CRON[17536]: (akudewan) CMD (/usr/local/bin/keeponline.sh 1> /dev/null 2> /dev/null)
Jul  2 13:10:01 ranjandesk /USR/SBIN/CRON[17790]: (akudewan) CMD (/usr/local/bin/keeponline.sh 1> /dev/null 2> /dev/null)
Jul  2 13:17:01 ranjandesk /USR/SBIN/CRON[17993]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jul  2 13:20:01 ranjandesk /USR/SBIN/CRON[18116]: (akudewan) CMD (/usr/local/bin/keeponline.sh 1> /dev/null 2> /dev/null)
Jul  2 13:30:01 ranjandesk /USR/SBIN/CRON[18399]: (akudewan) CMD (/usr/local/bin/keeponline.sh 1> /dev/null 2> /dev/null)
Jul  2 13:40:01 ranjandesk /USR/SBIN/CRON[18644]: (akudewan) CMD (/usr/local/bin/keeponline.sh 1> /dev/null 2> /dev/null)
Jul  2 13:50:01 ranjandesk /USR/SBIN/CRON[18943]: (akudewan) CMD (/usr/local/bin/keeponline.sh 1> /dev/null 2> /dev/null)

```

Anything else I can try ?

---

### Post by akudewan on 2008-07-03
*bump*

---

### Post by Gunman1982 on 2008-07-03
Show your crontab ('crontab -l')
append to the command you execute in the crontab the following: ' >> /dev/null 2>&1'
example:

40 * * * * /etc/init.d/whatever start >> /dev/null 2>&1

---

### Post by akudewan on 2008-07-03
Nope, still no go. It still shows the whole command is syslog.
```

Jul  3 23:06:01 ranjandesk /usr/sbin/cron[6459]: (akudewan) RELOAD (crontabs/akudewan)
Jul  3 23:10:01 ranjandesk /USR/SBIN/CRON[4835]: (akudewan) CMD (/usr/local/bin/keeponline.sh >> /dev/null 2>&1)

```

I haven't rebooted my machine since 3 days, maybe a reboot fix it ?

---

### Post by akudewan on 2008-07-04
Nope, reboot didn't fix it...

---

### Post by Gunman1982 on 2008-07-04
Oh ok, sry misunderstood what you want edit your '/etc/syslog.conf'

check for a line starting with 'cron' insert a # in front of the line

---

### Post by akudewan on 2008-07-04
Hi,

I still can't solve the problem.

This is what my /etc/syslog.conf looks like:
```

#  /etc/syslog.conf     Configuration file for syslogd.
#
#                       For more information see syslog.conf(5)
#                       manpage.

#
# First some standard logfiles.  Log by facility.
#

auth,authpriv.*                 /var/log/auth.log
*.*;auth,authpriv.none          -/var/log/syslog
[COLOR="Red"]#cron.*                         /var/log/cron.log[/COLOR]
daemon.*                        -/var/log/daemon.log
kern.*                          -/var/log/kern.log
lpr.*                           -/var/log/lpr.log
mail.*                          -/var/log/mail.log
user.*                          -/var/log/user.log

#
# Logging for the mail system.  Split it up so that
# it is easy to write scripts to parse these files.
#
mail.info                       -/var/log/mail.info
mail.warn                       -/var/log/mail.warn
mail.err                        /var/log/mail.err

# Logging for INN news system
#
news.crit                       /var/log/news/news.crit
news.err                        /var/log/news/news.err
news.notice                     -/var/log/news/news.notice

#
# Some `catch-all' logfiles.
#
*.=debug;\
        auth,authpriv.none;\
        news.none;mail.none     -/var/log/debug
*.=info;*.=notice;*.=warn;\
        auth,authpriv.none;\
[COLOR="Red"]#       cron,daemon.none;\[/COLOR]
        mail,news.none          -/var/log/messages

#
# Emergencies are sent to everybody logged in.
#
*.emerg                         *

#
# I like to have messages displayed on the console, but only on a virtual
# console I usually leave idle.
#
#daemon,mail.*;\
#       news.=crit;news.=err;news.=notice;\
#       *.=debug;*.=info;\
#       *.=notice;*.=warn       /dev/tty8

# The named pipe /dev/xconsole is for the `xconsole' utility.  To use it,
# you must invoke `xconsole' with the `-file' option:
#
#    $ xconsole -file /dev/xconsole [...]
#
# NOTE: adjust the list below, or you'll go crazy if you have a reasonably
#      busy site..
#
daemon.*;mail.*;\
        news.err;\
        *.=debug;*.=info;\
        *.=notice;*.=warn       |/dev/xconsole

```
(The lines in red are the cron entries commented out)

After this I ran "sudo /etc/init.d/sysklogd restart"

But my syslog still shows these entries:
```

Jul  4 18:36:58 ranjandesk exiting on signal 15
Jul  4 18:36:58 ranjandesk syslogd 1.5.0#1ubuntu1: restart.
Jul  4 18:40:01 ranjandesk /USR/SBIN/CRON[13768]: (akudewan) CMD (/usr/local/bin/keeponline.sh >> /dev/null 2>&1)
Jul  4 18:50:01 ranjandesk /USR/SBIN/CRON[13959]: (akudewan) CMD (/usr/local/bin/keeponline.sh >> /dev/null 2>&1)
Jul  4 19:00:01 ranjandesk /USR/SBIN/CRON[14116]: (akudewan) CMD (/usr/local/bin/keeponline.sh >> /dev/null 2>&1)
Jul  4 19:10:01 ranjandesk /USR/SBIN/CRON[14369]: (akudewan) CMD (/usr/local/bin/keeponline.sh >> /dev/null 2>&1)
Jul  4 19:17:01 ranjandesk /USR/SBIN/CRON[14502]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jul  4 19:20:01 ranjandesk /USR/SBIN/CRON[14546]: (akudewan) CMD (/usr/local/bin/keeponline.sh >> /dev/null 2>&1)
Jul  4 19:30:01 ranjandesk /USR/SBIN/CRON[14690]: (akudewan) CMD (/usr/local/bin/keeponline.sh >> /dev/null 2>&1)

```

:confused:

---

### Post by Gunman1982 on 2008-07-04
Did you restart your syslog daemon?
'sudo /etc/init.d/sysklogd restart'

---

### Post by akudewan on 2008-07-04
Yes, I did. (Mentioned in my previous post).

Btw, the cron man page gives an -L option to change the log level. But I have no idea how to use it...

---

### Post by akudewan on 2008-07-06
Problem solved!

In my /etc/syslog.conf file, I had to change the line from
```

*.*;auth,authpriv.none             -/var/log/syslog

```

to
```

*.*;auth,authpriv,**cron**.none             -/var/log/syslog

```

:)

---

### Post by motin on 2008-07-13
> **akudewan said:**
> Problem solved!

In my /etc/syslog.conf file, I had to change the line from
```

*.*;auth,authpriv.none             -/var/log/syslog

```

to
```

*.*;auth,authpriv,**cron**.none             -/var/log/syslog

```

:)

Nice! But I think the correct way would be:
```

*.*;auth,authpriv.none,cron.none             -/var/log/syslog

```

Cheers!

---

### Post by mempman on 2008-07-13
> **motin said:**
> Nice! But I think the correct way would be:
```

*.*;auth,authpriv.none,cron.none             -/var/log/syslog

```

Cheers!

you prolly don't want to set up it like you have done above because your are blocking cron.*, which would mean that if you job produces some errors or what not then you will have no log to monitor.  Also, cron.none limits all other cron jobs from being monitored.  Instead I would recommend that you change your cron.none to :

cron.info                                    /dev/null
cron.notice                                  /dev/null

---

### Post by akudewan on 2008-07-14
> **mempman said:**
> you prolly don't want to set up it like you have done above because your are blocking cron.*, which would mean that if you job produces some errors or what not then you will have no log to monitor.  Also, cron.none limits all other cron jobs from being monitored.  Instead I would recommend that you change your cron.none to :

cron.info                                    /dev/null
cron.notice                                  /dev/null

Thanks for the suggestions. Actually, I was planning to modify the script to run in a loop instead of using cron.

---

