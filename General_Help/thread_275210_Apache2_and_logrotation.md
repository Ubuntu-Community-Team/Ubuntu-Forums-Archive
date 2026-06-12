---
title: "Apache2 and logrotation"
date: 2006-10-11
forum: General Help
---

### Post by hellmet on 2006-10-11
Please forgive me if this is the wrong place for this thread..

I have some problem with Apache2 and logrotation not rotating the
logs properly

my /etc/logrotate.d/apache2 file looks like this

```
/var/log/apache2/*.log {
        weekly
        missingok
        rotate 52
        compress
        #delaycompress
        notifempty
        create 640 root adm
        sharedscripts
        postrotate
                if [ -f /var/run/apache2.pid ]; then
                        /etc/init.d/apache2 restart > /dev/null
                fi
        endscript
}
/var/log/apache2/ecomzera.com/*.log {
        daily
        missingok
        rotate 100
        compress
        #delaycompress
        notifempty
        create 640 root adm
        sharedscripts
        postrotate
                if [ -f /var/run/apache2.pid ]; then
                        /etc/init.d/apache2 restart > /dev/null
                fi
        endscript
}
/var/log/apache2/live-tracker.com/*.log {
        daily
        missingok
        rotate 100
        compress
 rotate 100
        compress
        #delaycompress
        notifempty
        create 640 root adm
        sharedscripts
        postrotate
                if [ -f /var/run/apache2.pid ]; then
                        /etc/init.d/apache2 restart > /dev/null
                fi
        endscript
}
/var/log/apache2/adriti.com/*.log {
        daily
        missingok
        rotate 100
        compress
        #delaycompress
        notifempty
        create 640 root adm
        sharedscripts
        postrotate
                if [ -f /var/run/apache2.pid ]; then
                        /etc/init.d/apache2 restart > /dev/null
                fi
        endscript
}
/var/log/apache2/pickupflowers.com/*.log {
        daily
        missingok
        rotate 100
        compress
        #delaycompress
        notifempty
        create 640 root adm
notifempty
        create 640 root adm
        sharedscripts
        postrotate
                if [ -f /var/run/apache2.pid ]; then
                        /etc/init.d/apache2 restart > /dev/null
                fi
        endscript
}
/var/log/apache2/giftsnideas.com/*.log {
        daily
        missingok
        rotate 100
        compress
        #delaycompress
        notifempty
        create 640 root adm
        sharedscripts
        postrotate
                if [ -f /var/run/apache2.pid ]; then
                        /etc/init.d/apache2 restart > /dev/null
                fi
        endscript
}


```Logrotations works superb for the first two virtualhosts..
but never works, even with -force option ...

This is the first time I'm doing somthing like this..
Am I doing something wrong??

Do I need to add something else somewhere??

Isn't logrotate supposed to rotate everything its asked for?](*,)

---

### Post by hellmet on 2006-10-11
found the solution..
thanks anyway

---

