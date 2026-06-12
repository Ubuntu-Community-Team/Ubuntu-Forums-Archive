---
title: "What did I do to my rsyslog config to stop mail logging?"
date: 2014-05-21
forum: General Help
---

### Post by Ackis on 2014-05-21
Hello everyone, my config files are are the bottom of the post.

Somehow I managed to get my mail logging to stop working.  I'm not sure why.  Any mail errors are caught in error.all.log but nothing is being logged to /var/log/mail/

Also somewhat related, is there an easy way to verify which files are caught with logrotate/log analysis programs?

/etc/rsyslog.d/20-ufw.conf
```

# Log kernel generated UFW log messages to file
:msg,contains,"[UFW " /var/log/ufw.log


# Uncomment the following to stop logging anything that matches the last rule.
# Doing this will stop logging kernel generated UFW log messages to the file
# normally containing kern.* messages (eg, /var/log/kern.log)
& stop

```

/etc/rsyslog.d/postfix.conf
```

# Create an additional socket in postfix's chroot in order not to break
# mail logging when rsyslog is restarted.  If the directory is missing,
# rsyslog will silently skip creating the socket.
$AddUnixListenSocket /var/spool/postfix/dev/log

```

[http://pastebin.com/Xs4pu0Ah](http://pastebin.com/Xs4pu0Ah)

/etc/rsyslog.d/50-default.conf
```


[LIST=1]
[*][COLOR=#000000]#  Default rules for rsyslog.[/COLOR]
[*][COLOR=#000000]#[/COLOR]
[*][COLOR=#000000]#                       For more information see rsyslog.conf(5) and /etc/rsyslog.conf[/COLOR]
[*][COLOR=#000000]#       http://shallowsky.com/blog/linux/rsyslog-conf-tutorial.html[/COLOR]
[*][COLOR=#000000]# Facilities:[/COLOR]
[*][COLOR=#000000]#        auth, authpriv, cron, daemon, kern, lpr, mail, news, syslog, user, uucp and local0 through local7[/COLOR]
[*][COLOR=#000000]# Priorities:[/COLOR]
[*][COLOR=#000000]#       debug, info, notice, warning, err, crit, alert, emerg[/COLOR]
[*][COLOR=#000000]#[/COLOR]
[*]
[*][COLOR=#000000]# Catch-all log files in syslog[/COLOR]
[*][COLOR=#000000]# Auth, Mail and News have their own logging facilities[/COLOR]
[*][COLOR=#000000]*.*;\[/COLOR]
[*][COLOR=#000000]        auth,authpriv.none;\[/COLOR]
[*][COLOR=#000000]        mail,news.none\[/COLOR]
[*][COLOR=#000000]                                /var/log/syslog[/COLOR]
[*]
[*][COLOR=#000000]auth,authpriv.*                 /var/log/auth.log[/COLOR]
[*][COLOR=#000000]cron.*                          /var/log/cron.log[/COLOR]
[*][COLOR=#000000]daemon.*                        /var/log/daemon.log[/COLOR]
[*][COLOR=#000000]kern.*                          /var/log/kern.log[/COLOR]
[*][COLOR=#000000]lpr.*                           /var/log/lpr.log[/COLOR]
[*][COLOR=#000000]user.*                          /var/log/user.log[/COLOR]
[*]
[*][COLOR=#000000]# Logging for the mail system.[/COLOR]
[*][COLOR=#000000]mail.alert                      /var/log/mail/mail.alert[/COLOR]
[*][COLOR=#000000]mail.crit                       /var/log/mail/mail.crit[/COLOR]
[*][COLOR=#000000]mail.debug                      /var/log/mail/mail.debug[/COLOR]
[*][COLOR=#000000]mail.emerg                      /var/log/mail/mail.emerg[/COLOR]
[*][COLOR=#000000]mail.info                       /var/log/mail/mail.info[/COLOR]
[*][COLOR=#000000]mail.warning                    /var/log/mail/mail.warn[/COLOR]
[*][COLOR=#000000]mail.err                        /var/log/mail/mail.err[/COLOR]
[*][COLOR=#000000]mail.notice                     /var/log/mail/mail.notice[/COLOR]
[*]
[*][COLOR=#000000]# Logging for INN news system.[/COLOR]
[*]
[*][COLOR=#000000]news.alert                      /var/log/news/news.alert[/COLOR]
[*][COLOR=#000000]news.crit                       /var/log/news/news.crit[/COLOR]
[*][COLOR=#000000]news.debug                      /var/log/news/news.debug[/COLOR]
[*][COLOR=#000000]news.emerg                      /var/log/news/news.emerg[/COLOR]
[*][COLOR=#000000]news.info                       /var/log/news/news.info[/COLOR]
[*][COLOR=#000000]news.warning                    /var/log/news/news.warning[/COLOR]
[*][COLOR=#000000]news.err                        /var/log/news/news.err[/COLOR]
[*][COLOR=#000000]news.notice                     /var/log/news/news.notice[/COLOR]
[*]
[*][COLOR=#000000]# Some "catch-all" log files.[/COLOR]
[*][COLOR=#000000]*.=debug;\[/COLOR]
[*][COLOR=#000000]        auth,authpriv.none;\[/COLOR]
[*][COLOR=#000000]        news,mail.none[/COLOR]
[*][COLOR=#000000]                                /var/log/debug[/COLOR]
[*]
[*][COLOR=#000000]*.=info;*.=notice;\[/COLOR]
[*][COLOR=#000000]        auth,authpriv.none;\[/COLOR]
[*][COLOR=#000000]        cron,daemon.none;\[/COLOR]
[*][COLOR=#000000]        mail,news.none\[/COLOR]
[*][COLOR=#000000]                                /var/log/messages[/COLOR]
[*]
[*][COLOR=#000000]# Emergencies are sent to everybody logged in.[/COLOR]
[*][COLOR=#000000]*.emerg                         :omusrmsg:*[/COLOR]
[*]
[*][COLOR=#000000]# Only log emerg, err and warning to their own logs and not everything else.[/COLOR]
[*][COLOR=#000000]*.emerg                         /var/log/emerg.log[/COLOR]
[*]
[*][COLOR=#000000]& stop[/COLOR]
[*]
[*][COLOR=#000000]*.err;\[/COLOR]
[*][COLOR=#000000]        auth,authpriv.none;\[/COLOR]
[*][COLOR=#000000]        mail,news.none\[/COLOR]
[*][COLOR=#000000]                                /var/log/error.log[/COLOR]
[*]
[*][COLOR=#000000]*.err                           /var/log/error.all.log[/COLOR]
[*]
[*][COLOR=#000000]& stop[/COLOR]
[*]
[*][COLOR=#000000]*.warning;\[/COLOR]
[*][COLOR=#000000]        auth,authpriv.none;\[/COLOR]
[*][COLOR=#000000]        mail,news.none\[/COLOR]
[*][COLOR=#000000]                                /var/log/warning.log[/COLOR]
[*]
[*][COLOR=#000000]*.warning                       /var/log/warning.all.log[/COLOR]
[*]
[*][COLOR=#000000]& stop
[/COLOR]
[/LIST]

```

---

### Post by Habitual on 2014-05-21
Can't stress enough how important backups are prior to editing.

Here's a snippet from my mail server's stock /etc/rsyslog.d/50-default.conf file **for comparison**
using 
```
cat /etc/rsyslog.d/50-default.conf | grep -v "#" | sed '/^$/d'
...

*.*;auth,authpriv.none;local0.none;local1.none;mail.none        -/var/log/syslog
kern.*                -/var/log/kern.log
mail.*                -/var/log/mail.log
mail.err            /var/log/mail.err
news.crit            /var/log/news/news.crit
news.err            /var/log/news/news.err
news.notice            -/var/log/news/news.notice
*.emerg                                :omusrmsg:*
daemon.*;mail.*;\
    news.err;\
    *.=debug;*.=info;\

```

---

### Post by Ackis on 2014-05-21
> **Habitual said:**
> Can't stress enough how important backups are prior to editing.


I do have backups (original file).  Mail logging isn't critical to me, and with the current config I can't figure out what actually is wrong.  The ufw and postfix configuration files are default.

> **Habitual said:**
> 
Here's a snippet from my mail server's stock /etc/rsyslog.d/50-default.conf file **for comparison**
using 
```
cat /etc/rsyslog.d/50-default.conf | grep -v "#" | sed '/^$/d'
...

*.*;auth,authpriv.none;local0.none;local1.none;mail.none        -/var/log/syslog
kern.*                -/var/log/kern.log
mail.*                -/var/log/mail.log
mail.err            /var/log/mail.err
news.crit            /var/log/news/news.crit
news.err            /var/log/news/news.err
news.notice            -/var/log/news/news.notice
*.emerg                                :omusrmsg:*
daemon.*;mail.*;\
    news.err;\
    *.=debug;*.=info;\

```


This is the mail section from my config.  It's more explicit (logs to different files) but the main thing that is different is that it doesn't have the "-" in front.  From the docs:

> 
[COLOR=#555555][FONT=Arial]You may prefix each entry with the minus "-'' sign to omit syncing the file after every logging. Note that you might lose information if the system crashes right behind a write attempt. Nevertheless this might give you back some performance, especially if you run programs that use logging in a very verbose manner.[/FONT][/COLOR]

```

# Logging for the mail system.
mail.alert                      /var/log/mail/mail.alert
mail.crit                       /var/log/mail/mail.crit
mail.debug                      /var/log/mail/mail.debug
mail.emerg                      /var/log/mail/mail.emerg
mail.info                       /var/log/mail/mail.info
mail.warning                    /var/log/mail/mail.warn
mail.err                        /var/log/mail/mail.err
mail.notice                     /var/log/mail/mail.notice

```


Edit: The links in your signature are very helpful, I've been after something like ShellCheck.

---

### Post by Habitual on 2014-05-22
Are you sure that mail logging has stopped because of rsyslog?
Does ```
grep mail  /var/log/* -R | less
``` indicate anything?

and what's the output of 
```
rsyslogd -f /etc/rsyslog.d/postfix.conf -N 1
```?

Thanks.

---

### Post by Ackis on 2014-05-25
The first command grep produces some interesting output... it looks like there's binary in there.

However I've taken the extreme step of removing postfix and sendmail and trying to start from scratch.  I haven't reinstalled it yet but I'll post back when I've had a chance to work on it.

---

### Post by Ackis on 2014-06-03
After spending way too much time dealing with this, the simple fix was that the permissions on /var/log/mail/ somehow reverted to 750 and root:root :(

---

