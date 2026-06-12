---
title: "At some oment I got error  MySQL configuration not found. How to fix it ?"
date: 2024-10-27
forum: General Help
---

### Post by nilovsergey on 2024-10-27
In some moment my MySQL server stopped working(I have installed my home kubuntu 22.05  several months ago)


I check commands :


    # mysql
    ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)
    root@master-at-home:/path# mysql -h 127.0.0.1 -P 3306 -u root
    ERROR 2003 (HY000): Can't connect to MySQL server on '127.0.0.1:3306' (111)
    root@master-at-home:/path# sudo service mysql start
    Job for mysql.service failed because the control process exited with error code.
    See "systemctl status mysql.service" and "journalctl -xeu mysql.service" for details.
    root@master-at-home:/path# systemctl status mysql.service
    × mysql.service - MySQL Community Server
    Loaded: loaded (/lib/systemd/system/mysql.service; enabled; vendor preset: enabled)
    Active: failed (Result: exit-code) since Sun 2024-10-27 09:33:42 EET; 10s ago
    Process: 32412 ExecStartPre=/usr/share/mysql/mysql-systemd-start pre (code=exited, status=1/FAILURE)
    CPU: 2ms
    
    master-at-home systemd[1]: mysql.service: Scheduled restart job, restart counter is at 5.
    master-at-home systemd[1]: Stopped MySQL Community Server.
    master-at-home systemd[1]: mysql.service: Start request repeated too quickly.
    master-at-home systemd[1]: mysql.service: Failed with result 'exit-code'.
    master-at-home systemd[1]: Failed to start MySQL Community Server.
    root@master-at-home:/path# journalctl -xeu mysql.service
    &#9617;&#9617; The job identifier is 3931 and the job result is done.
    master-at-home systemd[1]: Starting MySQL Community Server...
    &#9617;&#9617; Subject: A start job for unit mysql.service has begun execution
    &#9617;&#9617; Defined-By: systemd
    &#9617;&#9617; Support: [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
    &#9617;&#9617;
    &#9617;&#9617; A start job for unit mysql.service has begun execution.
    &#9617;&#9617;
    &#9617;&#9617; The job identifier is 3931.
    master-at-home mysql-systemd-start[32412]: MySQL configuration not found at /etc/mysql/my.cnf. Please create one.
    master-at-home systemd[1]: mysql.service: Control process exited, code=exited, status=1/FAILURE
    &#9617;&#9617; Subject: Unit process exited
    &#9617;&#9617; Defined-By: systemd
    &#9617;&#9617; Support: [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
    &#9617;&#9617;
    &#9617;&#9617; An ExecStartPre= process belonging to unit mysql.service has exited.
    &#9617;&#9617;
    &#9617;&#9617; The process' exit code is 'exited' and its exit status is 1.
    master-at-home systemd[1]: mysql.service: Failed with result 'exit-code'.
    &#9617;&#9617; Subject: Unit failed
    &#9617;&#9617; Defined-By: systemd
    &#9617;&#9617; Support: [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
    &#9617;&#9617;
    &#9617;&#9617; The unit mysql.service has entered the 'failed' state with result 'exit-code'.
    master-at-home systemd[1]: Failed to start MySQL Community Server.
    &#9617;&#9617; Subject: A start job for unit mysql.service has failed
    &#9617;&#9617; Defined-By: systemd
    &#9617;&#9617; Support: [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
    &#9617;&#9617;
    &#9617;&#9617; A start job for unit mysql.service has finished with a failure.
    &#9617;&#9617;
    &#9617;&#9617; The job identifier is 3931 and the job result is failed.
    master-at-home systemd[1]: mysql.service: Scheduled restart job, restart counter is at 5.
    &#9617;&#9617; Subject: Automatic restarting of a unit has been scheduled
    &#9617;&#9617; Defined-By: systemd
    &#9617;&#9617; Support: [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
    &#9617;&#9617;
    &#9617;&#9617; Automatic restarting of the unit mysql.service has been scheduled, as the result for
    &#9617;&#9617; the configured Restart= setting for the unit.
    master-at-home systemd[1]: Stopped MySQL Community Server.
    &#9617;&#9617; Subject: A stop job for unit mysql.service has finished
    &#9617;&#9617; Defined-By: systemd
    &#9617;&#9617; Support: [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
    &#9617;&#9617;
    &#9617;&#9617; A stop job for unit mysql.service has finished.
    &#9617;&#9617;
    &#9617;&#9617; The job identifier is 4065 and the job result is done.
    master-at-home systemd[1]: mysql.service: Start request repeated too quickly.
    master-at-home systemd[1]: mysql.service: Failed with result 'exit-code'.
    &#9617;&#9617; Subject: Unit failed
    &#9617;&#9617; Defined-By: systemd
    &#9617;&#9617; Support: [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
    &#9617;&#9617;
    &#9617;&#9617; The unit mysql.service has entered the 'failed' state with result 'exit-code'.
    master-at-home systemd[1]: Failed to start MySQL Community Server.
    &#9617;&#9617; Subject: A start job for unit mysql.service has failed
    &#9617;&#9617; Defined-By: systemd
    &#9617;&#9617; Support: [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
    &#9617;&#9617;
    &#9617;&#9617; A start job for unit mysql.service has finished with a failure.
    &#9617;&#9617;
    &#9617;&#9617; The job identifier is 4065 and the job result is failed.


I found line :


     master-at-home mysql-systemd-start[32412]: MySQL configuration not found at /etc/mysql/my.cnf. Please create one.


I have no /etc/mysql/ subdirectory at all. I do not know why so and how restore /etc/mysql/my.cnf in my OS ?


    uname -a
    Linux master-at-home 6.5.0-35-generic #35~22.04.1-Ubuntu SMP PREEMPT_DYNAMIC Tue May  7 09:00:52 UTC 2 x86_64 x86_64 x86_64 GNU/Linux


I decided to upgrade my OS but got next errors in messages :




    path# sudo apt-get update
    Hit:1 [https://artifacts.elastic.co/packages/8.x/apt](https://artifacts.elastic.co/packages/8.x/apt) stable InRelease
    Hit:2 [http://ua.archive.ubuntu.com/ubuntu](http://ua.archive.ubuntu.com/ubuntu) jammy InRelease
    Hit:3 [https://dl.google.com/linux/chrome/deb](https://dl.google.com/linux/chrome/deb) stable InRelease
    Hit:4 [https://deb.nodesource.com/node_18.x](https://deb.nodesource.com/node_18.x) nodistro InRelease
    Hit:5 [https://ppa.launchpadcontent.net/giuspen/ppa/ubuntu](https://ppa.launchpadcontent.net/giuspen/ppa/ubuntu) jammy InRelease
    Hit:6 [https://ppa.launchpadcontent.net/ondrej/php/ubuntu](https://ppa.launchpadcontent.net/ondrej/php/ubuntu) jammy InRelease
    Hit:7 [https://ppa.launchpadcontent.net/openswoole/ppa/ubuntu](https://ppa.launchpadcontent.net/openswoole/ppa/ubuntu) jammy InRelease
    Reading package lists... Done
    path# sudo apt-get upgrade
    Reading package lists... Done
    Building dependency tree... Done
    Reading state information... Done
    Calculating upgrade... Done
    The following packages have been kept back:
      php-common php-mcrypt php-mongodb php8.2-mongodb php8.3-mcrypt php8.3-mongodb
    0 upgraded, 0 newly installed, 0 to remove and 6 not upgraded.
    3 not fully installed or removed.
    After this operation, 0 B of additional disk space will be used.
    Do you want to continue? [Y/n] Y
    Setting up mysql-server-8.0 (8.0.28-0ubuntu4) ...
    update-alternatives: error: alternative path /etc/mysql/mysql.cnf doesn't exist
    dpkg: error processing package mysql-server-8.0 (--configure):
     installed mysql-server-8.0 package post-installation script subprocess returned error exit status 2
    Setting up elasticsearch (8.15.3) ...
    /usr/share/elasticsearch/bin/elasticsearch-env: line 78: source: /etc/default/elasticsearch: is a directory
    dpkg: error processing package elasticsearch (--configure):
     installed elasticsearch package post-installation script subprocess returned error exit status 1
    dpkg: dependency problems prevent configuration of mysql-server:
     mysql-server depends on mysql-server-8.0; however:
      Package mysql-server-8.0 is not configured yet.
    
    dpkg: error processing package mysql-server (--configure):
     dependency problems - leaving unconfigured
    No apport report written because the error message indicates its a followup error from a previous failure.
    Errors were encountered while processing:
     mysql-server-8.0
     elasticsearch
     mysql-server
    E: Sub-process /usr/bin/dpkg returned an error code (1)


Are these issues related ? How that can be fixed ?

---

### Post by nilovsergey on 2024-10-27
I have default my sql instllation, without any specific options...

---

### Post by yancek on 2024-10-27
>  See "systemctl status mysql.service" and "journalctl -xeu mysql.service" for details

Did you find anything useful when you followed the suggestion above from your error reports?  Did you do the install according to the instructions at the Ubuntu site below?  There is a specific section on configuring mysql which would be useful for you to read.  The my.conf file being missing is something that should not happen.

[https://documentation.ubuntu.com/server/how-to/databases/install-mysql/?_ga=2.164631099.547644272.1730032559-1234211060.1662380174](https://documentation.ubuntu.com/server/how-to/databases/install-mysql/?_ga=2.164631099.547644272.1730032559-1234211060.1662380174)

If you used instructions or a tutorial from a different source, it would be useful to post a link to it.

---

### Post by westonparker on 2024-11-06
If you're facing the "MySQL configuration not found" error on Kubuntu 22.04, it often points to a missing or corrupted `my.cnf` file. To fix this, you can restore the default configuration, reinstall MySQL to regenerate the necessary files, or ensure all dependencies are up to date. Check logs in `/var/log/mysql/` for specific error details. If you need to share large log files or configurations for troubleshooting, use [Filemail]("https://www.filemail.com/")&#8212;it allows you to send files up to 5 GB quickly and securely.

---

