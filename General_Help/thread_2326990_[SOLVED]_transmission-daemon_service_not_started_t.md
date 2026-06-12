---
title: "[SOLVED] transmission-daemon service not started though it says it is"
date: 2016-06-06
forum: General Help
---

### Post by brazzmonkey on 2016-06-06
hi there,
i've been running transmission-daemon for quite a while on ubuntu server.
Lately I notice transmission-daemon service would not start (it's nowhere to be found in pstree). I don't get any error whatsoever...
```
sam@fluffy:~$ sudo service transmission-daemon start
transmission-daemon start/running
sam@fluffy:~$ pstree
init&#9472;&#9516;&#9472;acpid
     &#9500;&#9472;apache2&#9472;&#9472;&#9472;2*[apache2&#9472;&#9472;&#9472;26*[{apache2}]]
     &#9500;&#9472;atd
     &#9500;&#9472;bandwidthd&#9472;&#9516;&#9472;3*[bandwidthd&#9472;&#9472;&#9472;bandwidthd]
     &#9474;            &#9492;&#9472;bandwidthd
     &#9500;&#9472;cron
     &#9500;&#9472;dbus-daemon
     &#9500;&#9472;dhclient
     &#9500;&#9472;dnsmasq
     &#9500;&#9472;6*[getty]
     &#9500;&#9472;mount.ntfs
     &#9500;&#9472;ntpd
     &#9500;&#9472;polipo
     &#9500;&#9472;privoxy
     &#9500;&#9472;pure-ftpd&#9472;&#9472;&#9472;pure-ftpd&#9472;&#9472;&#9472;pure-ftpd
     &#9500;&#9472;rsyslogd&#9472;&#9472;&#9472;3*[{rsyslogd}]
     &#9500;&#9472;sshd&#9472;&#9472;&#9472;sshd&#9472;&#9472;&#9472;sshd&#9472;&#9472;&#9472;bash&#9472;&#9472;&#9472;pstree
     &#9500;&#9472;sudo&#9472;&#9472;&#9472;ngrok&#9472;&#9472;&#9472;7*[{ngrok}]
     &#9500;&#9472;systemd-logind
     &#9500;&#9472;systemd-udevd
     &#9500;&#9472;upstart-file-br
     &#9500;&#9472;upstart-socket-
     &#9492;&#9472;upstart-udev-br
sam@fluffy:~$ sudo service transmission-daemon stop
transmission-daemon stop/waiting

```
syslog gives:
```
Jun  6 22:38:32 fluffy kernel: [81562.266618] init: startpar-bridge (transmission-daemon--stopped) state changed from starting to security
Jun  6 22:38:32 fluffy kernel: [81562.266690] init: startpar-bridge (transmission-daemon--stopped) state changed from security to pre-start
Jun  6 22:38:32 fluffy kernel: [81562.266758] init: startpar-bridge (transmission-daemon--stopped) state changed from pre-start to spawned
Jun  6 22:38:32 fluffy kernel: [81562.268780] init: startpar-bridge (transmission-daemon--stopped) main process (7539)
Jun  6 22:38:32 fluffy kernel: [81562.268835] init: startpar-bridge (transmission-daemon--stopped) state changed from spawned to post-start
Jun  6 22:38:32 fluffy kernel: [81562.269237] init: startpar-bridge (transmission-daemon--stopped) state changed from post-start to running
Jun  6 22:38:32 fluffy kernel: [81562.269764] init: Handling started event
Jun  6 22:38:32 fluffy kernel: [81562.270424] init: startpar-bridge (transmission-daemon--stopped) main process (7539) exited normally
Jun  6 22:38:32 fluffy kernel: [81562.270583] init: startpar-bridge (transmission-daemon--stopped) goal changed from start to stop
Jun  6 22:38:32 fluffy kernel: [81562.270766] init: startpar-bridge (transmission-daemon--stopped) state changed from running to stopping
Jun  6 22:38:32 fluffy kernel: [81562.270938] init: Handling stopping event
Jun  6 22:38:32 fluffy kernel: [81562.271036] init: startpar-bridge (transmission-daemon--stopped) state changed from stopping to killed
Jun  6 22:38:32 fluffy kernel: [81562.271520] init: startpar-bridge (transmission-daemon--stopped) state changed from killed to post-stop
Jun  6 22:38:32 fluffy kernel: [81562.271685] init: startpar-bridge (transmission-daemon--stopped) state changed from post-stop to waiting
Jun  6 22:38:32 fluffy kernel: [81562.272481] init: Handling stopped event

```
transmission-daemon package is transmission-daemon_2.82-1.1ubuntu3.1 on amd64
Should you have any idea, please share it with me,

thanks.

---

### Post by papibe on 2016-06-06
Hi brazzmonkey.

Could you open run these commands, and paste back the results? (you can copy/paste the text)
```
lsb_release -a

uname -a

cat /etc/default/transmission-daemon
```
Regards.

---

### Post by brazzmonkey on 2016-06-07
Hi papibe,

here they are:
```
$ lsb_release -a                                                                                                                                                                                      
No LSB modules are available.                                                                                                                                                                                                           
Distributor ID: Ubuntu                                                                                                                                                                                                                  
Description:    Ubuntu 14.04.4 LTS                                                                                                                                                                                                      
Release:        14.04                                                                                                                                                                                                                   
Codename:       trusty   
```
```
$ uname -a  
Linux fluffy 3.13.0-87-generic #133-Ubuntu SMP Tue May 24 18:32:09 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux    
```
```
$ cat /etc/default/transmission-daemon                                                                                                                                                                                      
# defaults for transmission-daemon                                                                                                                                                                                                      
# sourced by /etc/init.d/transmission-daemon

# Change to 0 to disable daemon
ENABLE_DAEMON=1

# This directory stores some runtime information, like torrent files 
# and links to the config file, which itself can be found in 
# /etc/transmission-daemon/settings.json
CONFIG_DIR="/var/lib/transmission-daemon/info" 

# Default options for daemon, see transmission-daemon(1) for more options
OPTIONS="--config-dir $CONFIG_DIR --logfile /var/log/transmission.log"

# (optional) extra options to start-stop-daemon
#START_STOP_OPTIONS="--iosched idle --nicelevel 10"

```

---

### Post by papibe on 2016-06-07
Thanks.

It looks OK, except the logging options.
[LIST]
[*]Did you add debian-transmission to the syslog group?
[*]Did you create the initial log file on /var/log?
[/LIST]
If not, you won't be logging correctly. Let's do something simpler. Change the proper line on your /etc/default/transmission-dameon so it looks like this:
```
# Default options for daemon, see transmission-daemon(1) for more options
OPTIONS="--config-dir $CONFIG_DIR  [COLOR="#FF0000"]**--log-debug --logfile /tmp/transmission.log**[/COLOR]"

```
Now start transmission, give it a few seconds, and then post the content of the new log file: /tmp/transmission.log

Regards.

---

### Post by brazzmonkey on 2016-06-07
Many thanks for your help.
I've been wrong about the logging options, sorry about that (I set them hoping they would help me to figure out where the problem is).
I modified the file according to your guidance. But it is no use, transmission-daemon doesn't start at all:
```
sam@fluffy:~$ sudo nano /etc/default/transmission-daemon 
sam@fluffy:~$ sudo service transmission-daemon start
transmission-daemon start/running
sam@fluffy:~$ cat /tmp/transmission.log
cat: /tmp/transmission.log: No such file or directory
sam@fluffy:~$ sudo service transmission-daemon status
transmission-daemon start/running
sam@fluffy:~$ pstree
init&#9472;&#9516;&#9472;acpid
     &#9500;&#9472;apache2&#9472;&#9472;&#9472;2*[apache2&#9472;&#9472;&#9472;26*[{apache2}]]
     &#9500;&#9472;atd
     &#9500;&#9472;bandwidthd&#9472;&#9516;&#9472;3*[bandwidthd&#9472;&#9472;&#9472;bandwidthd]
     &#9474;            &#9492;&#9472;bandwidthd
     &#9500;&#9472;cron
     &#9500;&#9472;dbus-daemon
     &#9500;&#9472;dhclient
     &#9500;&#9472;dnsmasq
     &#9500;&#9472;6*[getty]
     &#9500;&#9472;mount.ntfs
     &#9500;&#9472;ntpd
     &#9500;&#9472;polipo
     &#9500;&#9472;privoxy&#9472;&#9472;&#9472;2*[{privoxy}]
     &#9500;&#9472;pure-ftpd
     &#9500;&#9472;rsyslogd&#9472;&#9472;&#9472;3*[{rsyslogd}]
     &#9500;&#9472;sshd&#9472;&#9472;&#9472;sshd&#9472;&#9472;&#9472;sshd&#9472;&#9472;&#9472;bash&#9472;&#9472;&#9472;pstree
     &#9500;&#9472;sudo&#9472;&#9472;&#9472;ngrok&#9472;&#9472;&#9472;7*[{ngrok}]
     &#9500;&#9472;systemd-logind
     &#9500;&#9472;systemd-udevd
     &#9500;&#9472;upstart-file-br
     &#9500;&#9472;upstart-socket-
     &#9492;&#9472;upstart-udev-br
```

Is there any way to trace what upstart actually does ?

---

### Post by papibe on 2016-06-07
Try this:
```
sudo update-rc.d -f transmission-daemon remove

sudo update-rc.d transmission-daemon defaults
```

---

### Post by brazzmonkey on 2016-06-07
Did that, didn't help...
```
sam@fluffy:~$ sudo update-rc.d -f transmission-daemon remove
 Removing any system startup links for /etc/init.d/transmission-daemon ...
   /etc/rc0.d/K20transmission-daemon
   /etc/rc1.d/K20transmission-daemon
   /etc/rc2.d/S20transmission-daemon
   /etc/rc3.d/S20transmission-daemon
   /etc/rc4.d/S20transmission-daemon
   /etc/rc5.d/S20transmission-daemon
   /etc/rc6.d/K20transmission-daemon
sam@fluffy:~$ sudo update-rc.d transmission-daemon defaults
 Adding system startup for /etc/init.d/transmission-daemon ...
   /etc/rc0.d/K20transmission-daemon -> ../init.d/transmission-daemon
   /etc/rc1.d/K20transmission-daemon -> ../init.d/transmission-daemon
   /etc/rc6.d/K20transmission-daemon -> ../init.d/transmission-daemon
   /etc/rc2.d/S20transmission-daemon -> ../init.d/transmission-daemon
   /etc/rc3.d/S20transmission-daemon -> ../init.d/transmission-daemon
   /etc/rc4.d/S20transmission-daemon -> ../init.d/transmission-daemon
   /etc/rc5.d/S20transmission-daemon -> ../init.d/transmission-daemon
sam@fluffy:~$ sudo service transmission-daemon restart
transmission-daemon stop/waiting
transmission-daemon start/running
sam@fluffy:~$ cat /tmp/transmission.log
cat: /tmp/transmission.log: No such file or directory
sam@fluffy:~$ sudo service transmission-daemon status
transmission-daemon start/running
sam@fluffy:~$ pstree
init&#9472;&#9516;&#9472;acpid
     &#9500;&#9472;apache2&#9472;&#9472;&#9472;2*[apache2&#9472;&#9472;&#9472;26*[{apache2}]]
     &#9500;&#9472;atd
     &#9500;&#9472;bandwidthd&#9472;&#9516;&#9472;3*[bandwidthd&#9472;&#9472;&#9472;bandwidthd]
     &#9474;            &#9492;&#9472;bandwidthd
     &#9500;&#9472;cron
     &#9500;&#9472;dbus-daemon
     &#9500;&#9472;dhclient
     &#9500;&#9472;dnsmasq
     &#9500;&#9472;6*[getty]
     &#9500;&#9472;mount.ntfs
     &#9500;&#9472;ntpd
     &#9500;&#9472;polipo
     &#9500;&#9472;privoxy&#9472;&#9472;&#9472;{privoxy}
     &#9500;&#9472;pure-ftpd
     &#9500;&#9472;rsyslogd&#9472;&#9472;&#9472;3*[{rsyslogd}]
     &#9500;&#9472;sshd&#9472;&#9472;&#9472;sshd&#9472;&#9472;&#9472;sshd&#9472;&#9472;&#9472;bash&#9472;&#9472;&#9472;pstree
     &#9500;&#9472;sudo&#9472;&#9472;&#9472;ngrok&#9472;&#9472;&#9472;7*[{ngrok}]
     &#9500;&#9472;systemd-logind
     &#9500;&#9472;systemd-udevd
     &#9500;&#9472;upstart-file-br
     &#9500;&#9472;upstart-socket-
     &#9492;&#9472;upstart-udev-br

```

---

### Post by papibe on 2016-06-07
How about cleaning the house:
```
sudo apt-get purge transmission-daemon transmission-common
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install transmission-daemon transmission-common
```

---

### Post by brazzmonkey on 2016-06-07
should i back up my *.torrent files first ?

---

### Post by papibe on 2016-06-07
Backing up the info directory would preserve the torrents, and their status (how much has been downloaded).

Something like this should work:
```
sudo rsync -av /var/lib/transmission-daemon/info/ ~/info/
```
Also, if your downloads are in /var/lib/transmission-daemon/downloads, you may need to backup that too.

To backup everything to your home directory:
```
sudo rsync -av /var/lib/transmission-daemon/ ~/transmission-daemon/
```

If you don't have enough space to backup them, just move then:
```
sudo mv -iv /var/lib/transmission-daemon  /var/lib/transmission-daemon.back
```

Regards.

---

### Post by brazzmonkey on 2016-06-07
Sorry for the late reply, my internet connection dropped.
Everything's just fine now. I should have purged and reinstalled in the first place...
I still don't know what happened, I don't remember transmission being updated recently.
Many many thanks for sharing your time and skills.
Best regards.

---

