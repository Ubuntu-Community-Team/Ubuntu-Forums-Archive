---
title: "Logrotate problem"
date: 2013-02-24
forum: General Help
---

### Post by johncc on 2013-02-24
Ubuntu 12.04 LTS

Why is logrotate rotating my file when it is set to weekly but the state file shows it rotated just two days ago?

in /etc/logrotate.d/apache2:
```
/var/log/apache2/*.log {
        weekly
        missingok
        rotate 52
        compress
        delaycompress
        notifempty
        create 640 root adm
        sharedscripts
        postrotate
                /etc/init.d/apache2 reload > /dev/null
        endscript
        prerotate
                if [ -d /etc/logrotate.d/httpd-prerotate ]; then \
                        run-parts /etc/logrotate.d/httpd-prerotate; \
                fi; \
        endscript
}

```

In the file /var/lib/logrotate/status (today is 2/24):
```
logrotate state -- version 2
"/var/log/apache2/access.log" 2013-2-22
...
```


And when I logrotate "trial run"  logrotate -d /etc/logrotate.conf :
```
rotating pattern: /var/log/apache2/*.log  weekly (52 rotations)
empty log files are not rotated, old logs are removed
considering log /var/log/apache2/access.log
  log needs rotating
...
```

But if I edit the status file and set state to 2013-2-24, it (properly) says "log does not need rotating".

I'm doing this testing as root, as the daily crontab would be doing it...

Thanks in advance,
John

---

### Post by johncc on 2013-02-25
Is there a different or more appropriate forum that I should try posting this in?  Thanks, John

---

### Post by matt_symes on 2013-02-25
Hi

I'm not sure why it rotated early but i can tell you then time of rotate is stored in

```
/var/lib/logrotate/status
```

You may want to look in there to see the how it rotates as i'm not sure if that is the next time to rotate or the last time of rotation.

Maybe that will give you some clues.

Kind regards

---

### Post by johncc on 2013-02-25
Thanks for the reply, but I covered that in my OP :-k

---

### Post by matt_symes on 2013-02-25
Hi
			 		   		 		 		> Thanks for the reply, but I covered that in my OP :-k

Oh Yeah. 

Must be time for me to go to bed then :D It is 2.30am.

Kind regards

---

### Post by kjohri on 2013-02-26
Files are rotated for multiple reasons like desired periodicity (daily, weekly, monthly, etc) and also the file size. That is, once the file exceeds a certain size, it is rotated. So one thing to check in /etc/logrotate.conf is whether there is a global size directive.

[http://www.softprayog.in/tutorials/logrotate]("http://www.softprayog.in/tutorials/logrotate")

---

### Post by johncc on 2013-02-28
Thanks, I found the problem.  I am wanting to rotate these logs on Fridays.  Logrotate's idea of "weekly" is in effect Sundays-only.  It's right in the manpage :)

"Log files are rotated if the current weekday is less than the weekday of the last rotation or if more than a week has passed"

So I will use a different approach (split out these files in a separate logrotate.conf and then run logrotate for it only on Fridays).

Cheers,
John

---

