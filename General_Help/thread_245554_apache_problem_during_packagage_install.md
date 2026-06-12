---
title: "apache problem during packagage install"
date: 2006-08-28
forum: General Help
---

### Post by Wallythander on 2006-08-28
I am somthing of a Linux n00b, I have been toying around with Linux for about a year now, when last night I installed Kubuntu. Today I am having a problem, whenever I try to install a package, any package, through the terminal, through Adept, or through Synaptic, it gives me an error message.  In the terminal it says 
" * Starting apache-ssl 1.3 web server...                             [fail]
invoke-rc.d: initscript apache-ssl, action "start" failed.
dpkg: error processing apache-ssl (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 apache-ssl
E: Sub-process /usr/bin/dpkg returned an error code (1)"
I have spent literally hours looking for a solution! please help!

---

### Post by Wallythander on 2006-08-28
Plz help!!!
Sorry for the bump!!!

---

### Post by Wallythander on 2006-08-29
is there anyone????

---

### Post by mssever on 2006-08-29
Certainly a strange problem. Does Synaptic report any broken packages?

It looks like there's a problem in /etc/init.d/apache-ssl. You might manually invoke that and see if/what errors you get.
```
sudo /etc/init.d/apache-ssl stop
sudo /etc/init.d/apache-ssl start
```
Personally, I would make upgrading to apache2 high priority.

Also, if you kill all apache processes before running Synaptic, it might work.

---

### Post by Wallythander on 2006-08-29
hmmmm, when I restart Apache, it simply says that it fails...
I am going to try to install Apache 2

---

### Post by Wallythander on 2006-08-29
ohhh, and it says that there were no processes to kill in /var/run/apache-ssl.pid

Code:
willy@willy-desktop:~$ sudo /etc/init.d/apache-ssl stop
Password:
 * Stopping apache-ssl 1.3 web server...                                        No process in pidfile `/var/run/apache-ssl.pid' found running; none killed.
                                                                         [ ok ]
willy@willy-desktop:~$ sudo /etc/init.d/apache-ssl start
 * Starting apache-ssl 1.3 web server...                                 [fail]
willy@willy-desktop:~$

---

### Post by mssever on 2006-08-29
The reason it said that there were no processes to kill is probably that apache wasn't running. Not surprising, since it hasn't wanted to start.

Try looking in the logs in /var/log/apache for error messages. If you don't find anything there, look in /var/log/daemon.log*, /var/log/messages*, and /var/log/syslog*.

Also, you might try starting apache thus: sudo apachectl start. But if it won't start the other way, it won't start this way either. But it might give you an error message--although Apache prefers to write error messages to logs rather than printing them.

---

### Post by Wallythander on 2006-08-30
Well, I looked, the firs log doesnt exist apperantly.  And the two others /var/log/daemon.log and /var/log/messages contain nothing related to apache that I can see.

---

### Post by mssever on 2006-08-30
OK, find your apache.conf file. I'm not sure exactly where it is in apache 1, but my guess is /etc/apache or /etc/httpd. The file might also be called httpd.conf. Look in the file for the line that says "ErrorLog." This will point you to the log file you need to look in.

---

