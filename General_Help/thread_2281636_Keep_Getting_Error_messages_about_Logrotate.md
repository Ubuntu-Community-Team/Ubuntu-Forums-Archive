---
title: "Keep Getting Error messages about Logrotate"
date: 2015-06-08
forum: General Help
---

### Post by Leberyo on 2015-06-08
Once a day, I get an email with the following message in it:


```
/etc/cron.daily/logrotate: 
error: error running shared postrotate script for '/var/log/nginx/*.log ' 
run-parts: /etc/cron.daily/logrotate exited with return code 1 

```

The title of the email is: Cron <root@**myserver**> test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.daily )

Would anybody know the solution to this?

---

### Post by ian-weisser on 2015-06-10
Do you have nginx installed? Do you use it?

---

### Post by Leberyo on 2015-06-14
I do have Nginx installed.
I've figured out that the issue had to do with nginx logfile permissions.
The log files were owned by ww-data:adm. When I did chown root:root on the log files, the error messages disappeared for about a week.
A couple of days ago or so after doing nginx -t and reload, I got the the logrotate error email notification once again. Taking a look at one of the logs, it seems that one of them was changed to ww-data:adm instead of root:root. 

What would cause a change of ownership on these files?

---

### Post by Steve_Horan on 2015-06-14
nginx typically should not be using root... they typically run ass the www-data user or another service account. Running nginx externally facing as root has serious security implication.It is possible that your logs are being created under the service account. You can see the config for which user nginx is running in nginx.conf file.

---

### Post by Leberyo on 2015-06-14
Running htop, I can see that Nginx is not running under root but under the user.
Nginx.conf does specify the name of the user that runs Nginx. Does that mean that I need to do a chown "user":"user" on the log files?

---

### Post by Leberyo on 2015-06-14
I see that the nginx file under logrotate.d specifies:

  GNU nano 2.2.6                                  File: nginx                                                                           

/var/log/nginx/*.log {
        weekly
        missingok
        rotate 52
        compress
        delaycompress
        notifempty
        create 0640 www-data adm
        sharedscripts
        prerotate
                if [ -d /etc/logrotate.d/httpd-prerotate ]; then \
                        run-parts /etc/logrotate.d/httpd-prerotate; \
                fi \
        endscript
        postrotate
                invoke-rc.d nginx rotate >/dev/null 2>&1
        endscript
}


Which I think is wrong.

---

### Post by Leberyo on 2015-06-14
I think the permissions on the /var/log/nginx folder was incorrect.
I did a chown www-data:adm nginx and I'm pretty sure it should be ok from here on out. I kept the file ownerships as is inside this folder. They were owned by root:root and had 640 permissions.

---

