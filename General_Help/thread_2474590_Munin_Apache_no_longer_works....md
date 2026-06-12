---
title: "Munin: Apache no longer works..."
date: 2022-05-03
forum: General Help
---

### Post by wyattwhiteeagle on 2022-05-03
It looks like apache needs to be reconfigured, any suggestions?

It worked before and I could see munin's graph's and number's.
But now I get the following...

Upon reboot, I see this...
```
[Failed] Failed to start The Apache HTTP Server
```
From web browser (Google Chrome)
I changed my localhost IP for this post
```
This site can&#8217;t be reached
xxx.xxx.xxx.xx refused to connect.


Try:


Checking the connection
Checking the proxy and the firewall


ERR_CONNECTION_REFUSED


Check your Internet connection
Check any cables and reboot any routers, modems, or other network devices you may be using.


Allow Chrome to access the network in your firewall or antivirus settings.
If it is already listed as a program allowed to access the network, try removing it from the list and adding it again.


If you use a proxy server&#8230;
Check your proxy settings or contact your network administrator to make sure the proxy server is working. If you don't believe you should be using a proxy server: Go to the Chrome menu > Settings > Show advanced settings&#8230; > Change proxy settings&#8230; and make sure your configuration is set to "no proxy" or "direct."
```
From QTerminal
```
wyatt@wyatt-latitudee5400:~$ sudo systemctl restart apache2
[sudo] password for wyatt:           
Job for apache2.service failed because the control process exited with error code.
See "systemctl status apache2.service" and "journalctl -xeu apache2.service" for details.
wyatt@wyatt-latitudee5400:~$ sudo systemctl restart munin-node
wyatt@wyatt-latitudee5400:~$ 
```
From tac /var/log/syslog
```
May  3 04:50:35 wyatt-latitudee5400 systemd[1]: Failed to start The Apache HTTP Server.
May  3 04:50:35 wyatt-latitudee5400 systemd[1]: apache2.service: Failed with result 'exit-code'.
May  3 04:50:35 wyatt-latitudee5400 systemd[1]: apache2.service: Control process exited, code=exited, status=1/FAILURE
May  3 04:50:35 wyatt-latitudee5400 apachectl[651]: The Apache error log may have more information.
May  3 04:50:35 wyatt-latitudee5400 apachectl[651]: Action 'start' failed.
May  3 04:50:35 wyatt-latitudee5400 apachectl[682]: AH00014: Configuration check failed
May  3 04:50:35 wyatt-latitudee5400 apachectl[682]: (2)No such file or directory: AH02291: Cannot access directory '/var/log/apache2/' for error log of vhost defined at /etc/apache2/sites-enabled/000-default.conf:1
May  3 04:50:35 wyatt-latitudee5400 apachectl[682]: (2)No such file or directory: AH02291: Cannot access directory '/var/log/apache2/' for main error log
May  3 04:50:35 wyatt-latitudee5400 apachectl[682]: AH00558: apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1. Set the 'ServerName' directive globally to suppress this message
```
From systemctl status apache2.service
```
× apache2.service - The Apache HTTP Server
     Loaded: loaded (/lib/systemd/system/apache2.service; enabled; vendor preset: enabled)
     Active: failed (Result: exit-code) since Tue 2022-05-03 05:30:13 EDT; 4min 33s ago
       Docs: https://httpd.apache.org/docs/2.4/
    Process: 13765 ExecStart=/usr/sbin/apachectl start (code=exited, status=1/FAILURE)
        CPU: 26ms


May 03 05:30:13 wyatt-latitudee5400 systemd[1]: Starting The Apache HTTP Server...
May 03 05:30:13 wyatt-latitudee5400 apachectl[13768]: AH00558: apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1. Set the 'ServerName' directive globally to suppress this message
May 03 05:30:13 wyatt-latitudee5400 apachectl[13768]: (2)No such file or directory: AH02291: Cannot access directory '/var/log/apache2/' for main error log
May 03 05:30:13 wyatt-latitudee5400 apachectl[13768]: (2)No such file or directory: AH02291: Cannot access directory '/var/log/apache2/' for error log of vhost defined at /etc/apache2/sites-enabled/000-default.conf:1
May 03 05:30:13 wyatt-latitudee5400 apachectl[13768]: AH00014: Configuration check failed
May 03 05:30:13 wyatt-latitudee5400 apachectl[13765]: Action 'start' failed.
May 03 05:30:13 wyatt-latitudee5400 apachectl[13765]: The Apache error log may have more information.
May 03 05:30:13 wyatt-latitudee5400 systemd[1]: apache2.service: Control process exited, code=exited, status=1/FAILURE
May 03 05:30:13 wyatt-latitudee5400 systemd[1]: apache2.service: Failed with result 'exit-code'.
May 03 05:30:13 wyatt-latitudee5400 systemd[1]: Failed to start The Apache HTTP Server.
```
From journalctl -xeu apache2.service
```
May 03 05:18:53 wyatt-latitudee5400 systemd[1]: Starting The Apache HTTP Server...
&#9617;&#9617; Subject: A start job for unit apache2.service has begun execution
&#9617;&#9617; Defined-By: systemd
&#9617;&#9617; Support: http://www.ubuntu.com/support
&#9617;&#9617; 
&#9617;&#9617; A start job for unit apache2.service has begun execution.
&#9617;&#9617; 
&#9617;&#9617; The job identifier is 107.
May 03 05:19:01 wyatt-latitudee5400 apachectl[668]: AH00558: apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1. Set the 'ServerName' directive globally to suppress this message
May 03 05:19:01 wyatt-latitudee5400 apachectl[668]: (2)No such file or directory: AH02291: Cannot access directory '/var/log/apache2/' for main error log
May 03 05:19:01 wyatt-latitudee5400 apachectl[668]: (2)No such file or directory: AH02291: Cannot access directory '/var/log/apache2/' for error log of vhost defined at /etc/apache2/sites-enabled/000-default.conf:1
May 03 05:19:01 wyatt-latitudee5400 apachectl[668]: AH00014: Configuration check failed
May 03 05:19:01 wyatt-latitudee5400 apachectl[626]: Action 'start' failed.
May 03 05:19:01 wyatt-latitudee5400 apachectl[626]: The Apache error log may have more information.
May 03 05:19:01 wyatt-latitudee5400 systemd[1]: apache2.service: Control process exited, code=exited, status=1/FAILURE
&#9617;&#9617; Subject: Unit process exited
&#9617;&#9617; Defined-By: systemd
&#9617;&#9617; Support: http://www.ubuntu.com/support
&#9617;&#9617; 
&#9617;&#9617; An ExecStart= process belonging to unit apache2.service has exited.
&#9617;&#9617; 
&#9617;&#9617; The process' exit code is 'exited' and its exit status is 1.
May 03 05:19:01 wyatt-latitudee5400 systemd[1]: apache2.service: Failed with result 'exit-code'.
&#9617;&#9617; Subject: Unit failed
&#9617;&#9617; Defined-By: systemd
&#9617;&#9617; Support: http://www.ubuntu.com/support
&#9617;&#9617; 
&#9617;&#9617; The unit apache2.service has entered the 'failed' state with result 'exit-code'.
May 03 05:19:01 wyatt-latitudee5400 systemd[1]: Failed to start The Apache HTTP Server.
&#9617;&#9617; Subject: A start job for unit apache2.service has failed
&#9617;&#9617; Defined-By: systemd
&#9617;&#9617; Support: http://www.ubuntu.com/support
&#9617;&#9617; 
&#9617;&#9617; A start job for unit apache2.service has finished with a failure.
&#9617;&#9617; 
&#9617;&#9617; The job identifier is 107 and the job result is failed.
May 03 05:30:13 wyatt-latitudee5400 systemd[1]: Starting The Apache HTTP Server...
&#9617;&#9617; Subject: A start job for unit apache2.service has begun execution
&#9617;&#9617; Defined-By: systemd
&#9617;&#9617; Support: http://www.ubuntu.com/support
&#9617;&#9617; 
&#9617;&#9617; A start job for unit apache2.service has begun execution.
&#9617;&#9617; 
&#9617;&#9617; The job identifier is 1173.
May 03 05:30:13 wyatt-latitudee5400 apachectl[13768]: AH00558: apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1. Set the 'ServerName' directive globally to suppress this message
May 03 05:30:13 wyatt-latitudee5400 apachectl[13768]: (2)No such file or directory: AH02291: Cannot access directory '/var/log/apache2/' for main error log
May 03 05:30:13 wyatt-latitudee5400 apachectl[13768]: (2)No such file or directory: AH02291: Cannot access directory '/var/log/apache2/' for error log of vhost defined at /etc/apache2/sites-enabled/000-default.conf:1
May 03 05:30:13 wyatt-latitudee5400 apachectl[13768]: AH00014: Configuration check failed
May 03 05:30:13 wyatt-latitudee5400 apachectl[13765]: Action 'start' failed.
May 03 05:30:13 wyatt-latitudee5400 apachectl[13765]: The Apache error log may have more information.
May 03 05:30:13 wyatt-latitudee5400 systemd[1]: apache2.service: Control process exited, code=exited, status=1/FAILURE
&#9617;&#9617; Subject: Unit process exited
&#9617;&#9617; Defined-By: systemd
&#9617;&#9617; Support: http://www.ubuntu.com/support
&#9617;&#9617; 
&#9617;&#9617; An ExecStart= process belonging to unit apache2.service has exited.
&#9617;&#9617; 
&#9617;&#9617; The process' exit code is 'exited' and its exit status is 1.
May 03 05:30:13 wyatt-latitudee5400 systemd[1]: apache2.service: Failed with result 'exit-code'.
&#9617;&#9617; Subject: Unit failed
&#9617;&#9617; Defined-By: systemd
&#9617;&#9617; Support: http://www.ubuntu.com/support
&#9617;&#9617; 
&#9617;&#9617; The unit apache2.service has entered the 'failed' state with result 'exit-code'.
May 03 05:30:13 wyatt-latitudee5400 systemd[1]: Failed to start The Apache HTTP Server.
&#9617;&#9617; Subject: A start job for unit apache2.service has failed
&#9617;&#9617; Defined-By: systemd
&#9617;&#9617; Support: http://www.ubuntu.com/support
&#9617;&#9617; 
&#9617;&#9617; A start job for unit apache2.service has finished with a failure.
&#9617;&#9617; 
&#9617;&#9617; The job identifier is 1173 and the job result is failed.
```

---

### Post by wyattwhiteeagle on 2022-05-03
A couple links that may help me out here...

[https://ubuntuforums.org/showthread.php?t=2467076&page=2&highlight=apache2](https://ubuntuforums.org/showthread.php?t=2467076&page=2&highlight=apache2)

[https://discourse.lubuntu.me/t/new-installation-apache2-fails-to-start/2727](https://discourse.lubuntu.me/t/new-installation-apache2-fails-to-start/2727)

---

### Post by wyattwhiteeagle on 2022-05-05
> **ActionParsnip said:**
> What is the output of:
```

ps -ef | grep apache | grep -v apache
apt-cache policy apache2
lsb_release -a
uname -a

```
Thanks


ps -ef | grep apache | grep -v apache
No output


apt-cache policy apache2
```
apache2:
  Installed: 2.4.52-1ubuntu4
  Candidate: 2.4.52-1ubuntu4
  Version table:
 *** 2.4.52-1ubuntu4 500
        500 http://us.archive.ubuntu.com/ubuntu jammy/main amd64 Packages
        100 /var/lib/dpkg/status

```


lsb_release -a > /home/wyatt/Desktop/lsb-release.txt
```
Distributor ID:	Ubuntu
Description:	Ubuntu 22.04 LTS
Release:	22.04
Codename:	jammy
No LSB modules are available.
```


uname -a
```
Linux wyatt-latitudee5400 5.15.0-27-generic #28-Ubuntu SMP Thu Apr 14 04:55:28 UTC 2022 x86_64 x86_64 x86_64 GNU/Linux
```


I quoted the questions from the thread below and answered them...
[https://discourse.lubuntu.me/t/new-installation-apache2-fails-to-start/2727](https://discourse.lubuntu.me/t/new-installation-apache2-fails-to-start/2727)


> ...Do you see it running at all when using either top command or ps command?
There is no entry in htop for apache


> you can start it via systemctl command.
```
wyatt@wyatt-latitudee5400:~$ sudo systemctl restart apache2
[sudo] password for wyatt:           
Job for apache2.service failed because the control process exited with error code.
See "systemctl status apache2.service" and "journalctl -xeu apache2.service" for details.
wyatt@wyatt-latitudee5400:~$ sudo systemctl restart munin-node
wyatt@wyatt-latitudee5400:~$ 
```


> Otherwise, you can maybe check the log file at /var/log/messages 
but I don’t recall if that’s where Apache sends its logs. 
There might be an apache folder or httpd folder in that same location though (for Apache logs).
There is no such log or folder...
```
wyatt@wyatt-latitudee5400:~$ ls /var/log
apport.log    boot.log.1  gpu-manager.log  private                     wtmp
apport.log.1  btmp        kern.log         syslog                      Xorg.0.log
auth.log      cups        lastlog          ubuntu-advantage-timer.log  Xorg.0.log.old
boot.log      dmesg       munin            unattended-upgrades
wyatt@wyatt-latitudee5400:~$ 
```


> Also, Apache won’t start automatically after reboot unless you tell Systemd (the service+system manager) to start it for you.
I only believe I have this set because of the message at reboot...
```
[Failed] Failed to start The Apache HTTP Server
```


systemctl status apache2 > /home/wyatt/Desktop/ApacheStatus.txt
```
× apache2.service - The Apache HTTP Server
     Loaded: loaded (/lib/systemd/system/apache2.service; enabled; vendor preset: enabled)
     Active: failed (Result: exit-code) since Thu 2022-05-05 01:02:37 EDT; 8h ago
       Docs: https://httpd.apache.org/docs/2.4/
    Process: 642 ExecStart=/usr/sbin/apachectl start (code=exited, status=1/FAILURE)
        CPU: 77ms


May 05 01:02:30 wyatt-latitudee5400 systemd[1]: Starting The Apache HTTP Server...
May 05 01:02:37 wyatt-latitudee5400 apachectl[671]: AH00558: apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1. Set the 'ServerName' directive globally to suppress this message
May 05 01:02:37 wyatt-latitudee5400 apachectl[671]: (2)No such file or directory: AH02291: Cannot access directory '/var/log/apache2/' for main error log
May 05 01:02:37 wyatt-latitudee5400 apachectl[671]: (2)No such file or directory: AH02291: Cannot access directory '/var/log/apache2/' for error log of vhost defined at /etc/apache2/sites-enabled/000-default.conf:1
May 05 01:02:37 wyatt-latitudee5400 apachectl[671]: AH00014: Configuration check failed
May 05 01:02:37 wyatt-latitudee5400 apachectl[642]: Action 'start' failed.
May 05 01:02:37 wyatt-latitudee5400 apachectl[642]: The Apache error log may have more information.
May 05 01:02:37 wyatt-latitudee5400 systemd[1]: apache2.service: Control process exited, code=exited, status=1/FAILURE
May 05 01:02:37 wyatt-latitudee5400 systemd[1]: apache2.service: Failed with result 'exit-code'.
May 05 01:02:37 wyatt-latitudee5400 systemd[1]: Failed to start The Apache HTTP Server.
```

---

### Post by wyattwhiteeagle on 2022-05-05
Ok...
I have compiled quite a number of reports.

I can see that my issue is a configuration thing.

Have I shown enough info to see where the configuration's need to be modified?

---

### Post by dragonfly41 on 2022-05-05
I am coming in at tail end .. but reading above I would follow this advice ..

Job for apache2.service failed because the control process exited with error code.
See "systemctl status apache2.service" and "journalctl -xeu apache2.service" for details.

P.S. also run ..

[FONT=monospace][COLOR=#000000]sudo apachectl configtest[/COLOR]
[/FONT]

---

### Post by wyattwhiteeagle on 2022-05-05
> **dragonfly41 said:**
> I am coming in at tail end .. but reading above I would follow this advice ..


Job for apache2.service failed because the control process exited with error code.
See "systemctl status apache2.service" and "journalctl -xeu apache2.service" for details.


P.S. also run ..


sudo apachectl configtest



To bring these into focus...


sudo apachectl configtest
```
wyatt@wyatt-latitudee5400:~$ sudo apachectl configtest
[sudo] password for wyatt:           
AH00558: apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1. Set the 'ServerName' directive globally to suppress this message
(2)No such file or directory: AH02291: Cannot access directory '/var/log/apache2/' for main error log
(2)No such file or directory: AH02291: Cannot access directory '/var/log/apache2/' for error log of vhost defined at /etc/apache2/sites-enabled/000-default.conf:1
AH00014: Configuration check failed
Action 'configtest' failed.
The Apache error log may have more information.
wyatt@wyatt-latitudee5400:~$ 
```
systemctl status apache2.service
```
× apache2.service - The Apache HTTP Server
     Loaded: loaded (/lib/systemd/system/apache2.service; enabled; vendor preset: enabled)
     Active: failed (Result: exit-code) since Thu 2022-05-05 01:02:37 EDT; 9h ago
       Docs: https://httpd.apache.org/docs/2.4/
    Process: 642 ExecStart=/usr/sbin/apachectl start (code=exited, status=1/FAILURE)
        CPU: 77ms


May 05 01:02:30 wyatt-latitudee5400 systemd[1]: Starting The Apache HTTP Server...
May 05 01:02:37 wyatt-latitudee5400 apachectl[671]: AH00558: apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1. Set the 'ServerName' directive globally to suppress this message
May 05 01:02:37 wyatt-latitudee5400 apachectl[671]: (2)No such file or directory: AH02291: Cannot access directory '/var/log/apache2/' for main error log
May 05 01:02:37 wyatt-latitudee5400 apachectl[671]: (2)No such file or directory: AH02291: Cannot access directory '/var/log/apache2/' for error log of vhost defined at /etc/apache2/sites-enabled/000-default.conf:1
May 05 01:02:37 wyatt-latitudee5400 apachectl[671]: AH00014: Configuration check failed
May 05 01:02:37 wyatt-latitudee5400 apachectl[642]: Action 'start' failed.
May 05 01:02:37 wyatt-latitudee5400 apachectl[642]: The Apache error log may have more information.
May 05 01:02:37 wyatt-latitudee5400 systemd[1]: apache2.service: Control process exited, code=exited, status=1/FAILURE
May 05 01:02:37 wyatt-latitudee5400 systemd[1]: apache2.service: Failed with result 'exit-code'.
May 05 01:02:37 wyatt-latitudee5400 systemd[1]: Failed to start The Apache HTTP Server.
```
journalctl -xeu apache2.service
```
May 05 01:02:30 wyatt-latitudee5400 systemd[1]: Starting The Apache HTTP Server...
&#9617;&#9617; Subject: A start job for unit apache2.service has begun execution
&#9617;&#9617; Defined-By: systemd
&#9617;&#9617; Support: http://www.ubuntu.com/support
&#9617;&#9617; 
&#9617;&#9617; A start job for unit apache2.service has begun execution.
&#9617;&#9617; 
&#9617;&#9617; The job identifier is 135.
May 05 01:02:37 wyatt-latitudee5400 apachectl[671]: AH00558: apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1. Set the 'ServerName' directive globally to suppress this message
May 05 01:02:37 wyatt-latitudee5400 apachectl[671]: (2)No such file or directory: AH02291: Cannot access directory '/var/log/apache2/' for main error log
May 05 01:02:37 wyatt-latitudee5400 apachectl[671]: (2)No such file or directory: AH02291: Cannot access directory '/var/log/apache2/' for error log of vhost defined at /etc/apache2/sites-enabled/000-default.conf:1
May 05 01:02:37 wyatt-latitudee5400 apachectl[671]: AH00014: Configuration check failed
May 05 01:02:37 wyatt-latitudee5400 apachectl[642]: Action 'start' failed.
May 05 01:02:37 wyatt-latitudee5400 apachectl[642]: The Apache error log may have more information.
May 05 01:02:37 wyatt-latitudee5400 systemd[1]: apache2.service: Control process exited, code=exited, status=1/FAILURE
&#9617;&#9617; Subject: Unit process exited
&#9617;&#9617; Defined-By: systemd
&#9617;&#9617; Support: http://www.ubuntu.com/support
&#9617;&#9617; 
&#9617;&#9617; An ExecStart= process belonging to unit apache2.service has exited.
&#9617;&#9617; 
&#9617;&#9617; The process' exit code is 'exited' and its exit status is 1.
May 05 01:02:37 wyatt-latitudee5400 systemd[1]: apache2.service: Failed with result 'exit-code'.
&#9617;&#9617; Subject: Unit failed
&#9617;&#9617; Defined-By: systemd
&#9617;&#9617; Support: http://www.ubuntu.com/support
&#9617;&#9617; 
&#9617;&#9617; The unit apache2.service has entered the 'failed' state with result 'exit-code'.
May 05 01:02:37 wyatt-latitudee5400 systemd[1]: Failed to start The Apache HTTP Server.
&#9617;&#9617; Subject: A start job for unit apache2.service has failed
&#9617;&#9617; Defined-By: systemd
&#9617;&#9617; Support: http://www.ubuntu.com/support
&#9617;&#9617; 
&#9617;&#9617; A start job for unit apache2.service has finished with a failure.
&#9617;&#9617; 
&#9617;&#9617; The job identifier is 135 and the job result is failed.

```

---

### Post by wyattwhiteeagle on 2022-05-05
The only instructions I see given by the system is...
> Set the 'ServerName' directive globally to suppress this message
Error logs need to be configured


How do I set the ServerName directive globally?


The error logs don't exist.
How do I create them or have them created?
If they existed, we might know more.


```
apachectl[671]: AH00558: apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1. Set the 'ServerName' directive globally to suppress this message
apachectl[671]: (2)No such file or directory: AH02291: Cannot access directory '/var/log/apache2/' for main error log
apachectl[671]: (2)No such file or directory: AH02291: Cannot access directory '/var/log/apache2/' for error log of vhost defined at /etc/apache2/sites-enabled/000-default.conf:1
```

---

### Post by wyattwhiteeagle on 2022-05-05
> file:///var/www/html/index.html

The file above contains the instruction in the quote that follows my questions.
I remember seeing the page but ignored it because I believed it was only informational.
The issue I'm having may be because I ignored the instructions.

The page state's...
> [COLOR=#000000]*You should replace this file (located at /var/www/html/index.html) before continuing to operate your HTTP server.*[/COLOR]

Is it saying to replace the file "index.html"?
What file needs to replace it?
What needs to be in the file that replaces it?

How do I [COLOR=#000000][FONT=Ubuntu]symlink available configuration files from their respective *-available/ counterparts?

[/FONT][/COLOR]What modications need to be made for calling [B]/usr/bin/apache2 to work?

[/B]How do I check to see if anything needs to be whitelisted?
What would I be looking for?
How do I whitelist these things?

I know some of this is very basic.
Even very basic things, if a person doesn't know about them or what to do...
then asking questions is sometimes beneficial.
I'm hoping that asking these questions will be beneficial for me.

I'm wanting to monitor only my laptop using Munin.
When I get it configured correctly, I can look into monitoring others on my local network.
My first goal is to get my own being monitored.

> Apache2 Default Page
It works!
This is the default welcome page used to test the correct operation of the Apache2 server after installation on Ubuntu systems. It is based on the equivalent page on Debian, from which the Ubuntu Apache packaging is derived. If you can read this page, it means that the Apache HTTP server installed at this site is working properly. You should replace this file (located at /var/www/html/index.html) before continuing to operate your HTTP server.


If you are a normal user of this web site and don't know what this page is about, this probably means that the site is currently unavailable due to maintenance. If the problem persists, please contact the site's administrator.


Configuration Overview
Ubuntu's Apache2 default configuration is different from the upstream default configuration, and split into several files optimized for interaction with Ubuntu tools. The configuration system is fully documented in /usr/share/doc/apache2/README.Debian.gz. Refer to this for the full documentation. Documentation for the web server itself can be found by accessing the manual if the apache2-doc package was installed on this server.


The configuration layout for an Apache2 web server installation on Ubuntu systems is as follows:

/etc/apache2/
|-- apache2.conf
|       `--  ports.conf
|-- mods-enabled
|       |-- *.load
|       `-- *.conf
|-- conf-enabled
|       `-- *.conf
|-- sites-enabled
|       `-- *.conf
          

apache2.conf is the main configuration file. It puts the pieces together by including all remaining configuration files when starting up the web server.

ports.conf is always included from the main configuration file. It is used to determine the listening ports for incoming connections, and this file can be customized anytime.

Configuration files in the mods-enabled/, conf-enabled/ and sites-enabled/ directories contain particular configuration snippets which manage modules, global configuration fragments, or virtual host configurations, respectively.

They are activated by symlinking available configuration files from their respective *-available/ counterparts. These should be managed by using our helpers a2enmod, a2dismod, a2ensite, a2dissite, and a2enconf, a2disconf . See their respective man pages for detailed information.

The binary is called apache2 and is managed using systemd, so to start/stop the service use systemctl start apache2 and systemctl stop apache2, and use systemctl status apache2 and journalctl -u apache2 to check status. system and apache2ctl can also be used for service management if desired. Calling /usr/bin/apache2 directly will not work with the default configuration.


Document Roots
By default, Ubuntu does not allow access through the web browser to any file outside of those located in /var/www, public_html directories (when enabled) and /usr/share (for web applications). If your site is using a web document root located elsewhere (such as in /srv) you may need to whitelist your document root directory in /etc/apache2/apache2.conf.

The default Ubuntu document root is /var/www/html. You can make your own virtual hosts under /var/www.

---

### Post by dragonfly41 on 2022-05-05
I trace back to your opening statement of goals ..

[https://ubuntuforums.org/showthread.php?t=2473706&highlight=munin](https://ubuntuforums.org/showthread.php?t=2473706&highlight=munin)

> Now that I'm beginning to "sober up" some of my Lubuntu 20.04 "drunkenness" to where it isn't "stumbling into so many walls".

I'm sure there are other issue's that I've missed.

But for now, I'm feeling the need to address performance bottlenecks of packages, applications and internet (Wifi).


Now you are pursuing munin ..
I have not installed munin myself ..

but I wonder if you might find webmin more useful to get a handle on all your resources.

After installation you access it through

sudo systemctl restart webmin

then in browser view

[https://localhost:10000](https://localhost:10000)


You might see a warning message in browser about security ([https://](https://)) but just clickthrough and you see a comprehensive control panel.

Through a control panel you can explore configurations, packages, servers, resources .. 

[https://phoenixnap.com/kb/install-webmin-on-ubuntu](https://phoenixnap.com/kb/install-webmin-on-ubuntu)

You can also build custom commands to run.

That would be my suggestion as starter. Then install munin through webmin.

Webmin and Munin are listed here.

[https://linuxhandbook.com/server-monitoring-tools/](https://linuxhandbook.com/server-monitoring-tools/)

---

### Post by SeijiSensei on 2022-05-05
> May 05 01:02:37 wyatt-latitudee5400 apachectl[671]: (2)No such file or directory: AH02291: Cannot access directory '/var/log/apache2/' for main error log
My guess is either that /var/log/apache2 doesn't exist or it has the wrong permissions. I just installed apache2 from scratch on this machine. It created
```

$ cd /var/log; ls -l | grep apache

drwxr-x---  2 root   adm                 4096 May  5 16:38 apache2
```

The logs it writes to that directory are all owned by root:adm.

---

### Post by dragonfly41 on 2022-05-06
Added tip:

In /etc/hosts  file ensure that there is at least this line included

127.0.0.1    localhost

If not your localhost server will not work.

And on setting this line ensure that you press F5 to refresh your browser cache.

---

### Post by wyattwhiteeagle on 2022-05-06
> **dragonfly41 said:**
> I trace back to your opening statement of goals ..

[https://ubuntuforums.org/showthread.php?t=2473706&highlight=munin](https://ubuntuforums.org/showthread.php?t=2473706&highlight=munin)



Now you are pursuing munin ..
I have not installed munin myself ..

but I wonder if you might find webmin more useful to get a handle on all your resources.

After installation you access it through

sudo systemctl restart webmin

then in browser view

[https://localhost:10000](https://localhost:10000)


You might see a warning message in browser about security ([https://](https://)) but just clickthrough and you see a comprehensive control panel.

Through a control panel you can explore configurations, packages, servers, resources .. 

[https://phoenixnap.com/kb/install-webmin-on-ubuntu](https://phoenixnap.com/kb/install-webmin-on-ubuntu)

You can also build custom commands to run.

That would be my suggestion as starter. Then install munin through webmin.

Webmin and Munin are listed here.

[https://linuxhandbook.com/server-monitoring-tools/](https://linuxhandbook.com/server-monitoring-tools/)

ok...
I have webmin installed and working after rebooting.
That link is an awesome tutorial for webmin.

I was needing something to monitor all the deep detailed stuff.

How do I install munin through webmin?

Looking through the different things in webmin, I didn't see an option to install other things.

---

### Post by wyattwhiteeagle on 2022-05-07
> **dragonfly41 said:**
> ...Then install munin through webmin...


ok...
How do I install munin through webmin?
Looking through the different things in webmin, I didn't see an option to install other things.

I seen options to configure things...but not to install things.

Did you mean configure munin through webmin?

---

### Post by dragonfly41 on 2022-05-07
> [COLOR=#000000]Did you mean configure munin through webmin?[/COLOR][COLOR=#000000]

Yes. Since you have access to all the tools through Webmin and you can check Apache servers.

But I will try to expand later if needed.

webmin is your "Swiss army knife" and you can edit configuration files.
I looked briefly for a munin module (webmin plugin) but did not find one. So a custom module is probably one way.
Or just use commands within webmin.[/COLOR]

---

### Post by dragonfly41 on 2022-05-07
[FONT=Verdana]Resubmitted after formatting glitch ..

I now have munin running after referring to guides found here ..[/FONT]

[FONT=Verdana]https://www.hackerxone.com/2021/10/14/steps-to-install-munin-monitoring-tool-on-ubuntu-20-04-lts/[/FONT]

[FONT=Verdana]https://wiki.debian.org/Munin/ApacheConfiguration[/FONT][FONT=Verdana]
[/FONT]
[FONT=Verdana]I used Webmin to edit files.[/FONT]

[FONT=Verdana]We can navigate to Custom Commands and click on toolbar > Create a new file editor[/FONT]

[FONT=Verdana]/etc/munin/apache24.conf[/FONT]

[FONT=Verdana]then navigate to select that file.[/FONT]
[FONT=Verdana]
[/FONT]
[FONT=Verdana]Now we see in Custom Commands list ..[/FONT]

[FONT=Verdana]/etc/munin/apache24.conf[/FONT]
[FONT=Verdana]
[/FONT]
[FONT=Verdana]Under the column Actions (to the far right) click on Open.[/FONT]
[FONT=Verdana]A window .. Edit File .. opens.[/FONT]
[FONT=Verdana]Syntax colouring can be set by clicking on Plain Text at top right [/FONT]
[FONT=Verdana]
[/FONT]
[FONT=Verdana]Choose a syntax which colours tags. And preferably fades out comments lines.[/FONT]
[FONT=Verdana]I could not find an ideal match and settled on HTML.[/FONT]
[FONT=Verdana]Embedded Javascript and LiveScript also seem to fit

[/FONT][P.S.] see another way at foot of this post.

[FONT=Verdana]I did not in fact follow the tutorial advice to edit Local but left the config file unchanged.[/FONT]

[FONT=Verdana]After starting munin I can go to ..[/FONT]

[FONT=Verdana]http://localhost/munin.[/FONT]

[FONT=Verdana]The benefit of Webmin is that it allows server processes to be checked.


[P.S.] Another way to edit /etc/munin/apache24.conf is through here in webmin .. with syntax colouring

[/FONT]https://localhost:10000/apache/allmanual_form.cgi?xnavigation=1

---

### Post by wyattwhiteeagle on 2022-05-07
> **dragonfly41 said:**
> [FONT=Verdana]Resubmitted after formatting glitch ..

I now have munin running after referring to guides found here ..[/FONT]

[FONT=Verdana]https://www.hackerxone.com/2021/10/14/steps-to-install-munin-monitoring-tool-on-ubuntu-20-04-lts/[/FONT]

[FONT=Verdana]https://wiki.debian.org/Munin/ApacheConfiguration[/FONT][FONT=Verdana]
[/FONT]
A formatting glitch...
No wonder I kept running into errors and having failure.

Let me try what you found and I will report back.
I have a family function to attend this afternoon, so it will be sometime tonight or tomorrow when I try it.

---

### Post by dragonfly41 on 2022-05-07
My formatting glitch was simply too much whitespace in my forum post .. for some reason .. now corrected.
Nothing to do with munin/webmin.

---

### Post by wyattwhiteeagle on 2022-05-07
I tried it...it worked

I rebooted...it worked

I ran bleachbit, stacer, a custom cleanup package mangement script then rebooted then ran...

```
sudo apt update && sudo apt full-upgrade -y
```

Now I'm back at the "ERR_CONNECTION_REFUSED" when I run [http://localhost/munin](http://localhost/munin) in the web browser.

It seems that something in bleachbit, stacer, or my custom script is knocking something out causing it not to work.

I need to start getting ready for that family function.
I'll do further troubleshooting after returning home tonight.

---

### Post by wyattwhiteeagle on 2022-05-09
Well folks...

I still have a lot of narrowing down to do.

Here's what I found so far...

My custom script doesn't break Munin.
Bleachbit doesn't break Munin
Stacer is the culprit

The only thing in Stacer that breaks Munin is clearing out the Application Caches all at once.

On my laptop, Stacer detects seven caches.
Clearing the individual caches one by one detected by stacer doesn't break Munin.
Clearing fontconfig cache in combination with one of the other caches doesnt break Munin.

So far the only culprit I found was clearing all of the application caches all at once.

I will keep drilling and post as I learn more.

---

### Post by dragonfly41 on 2022-05-09
I found this for reference and troubleshooting .. munin architecture ..

[http://guide.munin-monitoring.org/en/latest/architecture/index.html](http://guide.munin-monitoring.org/en/latest/architecture/index.html)

---

### Post by wyattwhiteeagle on 2022-05-10
When we were working with Actiona, something was said along the lines of gathering the command lines for the scripts to use.

There are command line scripts being used when the system clean in Stacer is ran.

Would checking those command lines in Stacer help narrow down why Stacer keeps breaking the Apache2 HTTP Server, thus breaking Munin?

Where would Stacer's command line script's be located?

I may choose to only use Stacer as a reference to find other things.
Not actually running it's job commands.
But I want to check it's command line scripts before making that choice.

---

### Post by dragonfly41 on 2022-05-10
As reported in parallel thread ..

[COLOR=#000000]Some clues found ..[/COLOR]

[https://github.com/oguzhaninan/Stacer/issues/425](https://github.com/oguzhaninan/Stacer/issues/425)

Reset fresh log files.

---

