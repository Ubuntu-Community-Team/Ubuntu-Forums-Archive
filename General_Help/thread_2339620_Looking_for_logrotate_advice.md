---
title: "Looking for logrotate advice"
date: 2016-10-10
forum: General Help
---

### Post by rsodhia on 2016-10-10
I've been a webdev for a good number of years, and lately I've been trying to learn more about the server side of things beyond the basics (installing a LAMP stack, setting up apache to run a site, etc). One I'm having a lot of trouble with is logrotate, and I'm hoping I can get some advice here.




My apache (I'm guessing) came setup with this log rotate already:


```
/var/log/apache2/*.log {
     daily
     missingok
     compress
     delaycompress
     notifempty
     create 640 root adm
     sharedscripts
     postrotate
             if /etc/init.d/apache2 status &gt; /dev/null ; then \
                 /etc/init.d/apache2 reload &gt; /dev/null; \
             fi;
     endscript
     prerotate
             if [ -d /etc/logrotate.d/httpd-prerotate ]; then \
                     run-parts /etc/logrotate.d/httpd-prerotate; \
             fi; \
     endscript</div
}
```


The only difference is it had weekly and set to expire after 52 weeks. I wanted to change it to daily. I have my individual sites setup to log to subfolders from there, eg, /var/log/apache2/site1/. I was under the impression from trying to read the documentation on logrotate that the *.log would also match subfolders, but for the first time in a long time, I went to check, and there is only one error log, and it's huge. So I created a second logrotate file


```
/var/log/apache2/site1/*.log {
     daily
     missingok
     compress
     delaycompress
     notifempty
     create 640 root adm
     sharedscripts
     postrotate
             if /etc/init.d/apache2 status &gt; /dev/null ; then \
                 /etc/init.d/apache2 reload &gt; /dev/null; \
             fi;
     endscript
     prerotate
             if [ -d /etc/logrotate.d/httpd-prerotate ]; then \
                     run-parts /etc/logrotate.d/httpd-prerotate; \
             fi; \
     endscript
	}
```


But this doesn't seem to do anything to the files either. I'm not sure if I'm not understanding something about logrotate, or what... I appreciate any help.

---

### Post by SeijiSensei on 2016-10-11
Run logrotate from the command line in debug mode like this:

```
sudo logrotate -d -f /path/to/config_file.conf
```

The relevant file is /etc/logrotate.d/apache.  Don't modify the main /etc/logrotate.conf file, just the service-specific ones in /etc/logrotate.d/.  After you modify the "apache" file in that directory, you can test it with

```
sudo logrotate -d -f /etc/logrotate.d/apache
```

Type "man logrotate" at the prompt to see what the various options do.

---

### Post by rsodhia on 2016-10-11
I did go through the man file, but maybe it's just because I'm not used to it, I couldn't figure out how to put it together in a meaningful way. And I created my own config under logrotate.d; I'm not editing the default one. The result of the debug is vexing, given I'm running it as root?

```

reading config file /etc/logrotate.d/gamersplane


Handling 1 logs


rotating pattern: /var/log/apache2/gamersplane/*.log  forced from command line (no old logs will be kept)
empty log files are not rotated, old logs are removed
considering log /var/log/apache2/gamersplane/access.log
  log needs rotating
considering log /var/log/apache2/gamersplane/error.log
  log needs rotating
rotating log /var/log/apache2/gamersplane/access.log, log->rotateCount is 0
dateext suffix '-20161011'
glob pattern '-[0-9][0-9][0-9][0-9][0-9][0-9][0-9][0-9]'
compressing log with: /bin/gzip
renaming /var/log/apache2/gamersplane/access.log.1.gz to /var/log/apache2/gamersplane/access.log.2.gz (rotatecount 1, logstart 1, i 1), 
renaming /var/log/apache2/gamersplane/access.log.0.gz to /var/log/apache2/gamersplane/access.log.1.gz (rotatecount 1, logstart 1, i 0), 
rotating log /var/log/apache2/gamersplane/error.log, log->rotateCount is 0
dateext suffix '-20161011'
glob pattern '-[0-9][0-9][0-9][0-9][0-9][0-9][0-9][0-9]'
compressing log with: /bin/gzip
renaming /var/log/apache2/gamersplane/error.log.1.gz to /var/log/apache2/gamersplane/error.log.2.gz (rotatecount 1, logstart 1, i 1), 
renaming /var/log/apache2/gamersplane/error.log.0.gz to /var/log/apache2/gamersplane/error.log.1.gz (rotatecount 1, logstart 1, i 0), 
running prerotate script
running script with arg /var/log/apache2/gamersplane/*.log : "
                if [ -d /etc/logrotate.d/httpd-prerotate ]; then \
                        run-parts /etc/logrotate.d/httpd-prerotate; \
                fi; \
"
renaming /var/log/apache2/gamersplane/access.log to /var/log/apache2/gamersplane/access.log.1
disposeName will be /var/log/apache2/gamersplane/access.log.1.gz
creating new /var/log/apache2/gamersplane/access.log mode = 0640 uid = 0 gid = 4
renaming /var/log/apache2/gamersplane/error.log to /var/log/apache2/gamersplane/error.log.1
disposeName will be /var/log/apache2/gamersplane/error.log.1.gz
creating new /var/log/apache2/gamersplane/error.log mode = 0640 uid = 0 gid = 4
running postrotate script
running script with arg /var/log/apache2/gamersplane/*.log : "
                if /etc/init.d/apache2 status > /dev/null ; then \
                    /etc/init.d/apache2 reload > /dev/null; \
                fi;
"
removing old log /var/log/apache2/gamersplane/access.log.1.gz
error: error opening /var/log/apache2/gamersplane/access.log.1.gz: No such file or directory
```

It's having trouble removing the old access.log.1.gz, which doesn't exist, so it fails? But why is it looking for a file that doesn't exist?

---

### Post by SeijiSensei on 2016-10-12
It won't complain after the next rotation.

Did you get a /var/log/apache2/gamersplane/access.log.1.gz after running that?

---

