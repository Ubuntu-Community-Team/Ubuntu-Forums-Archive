---
title: "mysql Ver 14.14 Distrib 5.7.27 stops suddenly on ubuntu 18.04.3 LTS"
date: 2019-11-12
forum: General Help
---

### Post by marchello_lippi2 on 2019-11-12
Hi all, 
I encoutered issue that mysql Ver 14.14 Distrib 5.7.27 stops suddenly on ubuntu 18.04.3 LTS. 
Will add logs here.

Is it any known issue already?

Upd: Syslog is below. Reboot helped me, but this is just a workaround. Please advise.
> 
Nov 12 05:01:03 m3a systemd[1]: Starting MySQL Community Server...
Nov 12 05:01:03 m3a kernel: [316377.797698] audit: type=1400 audit(1573527663.497:21): apparmor="DENIED" operation="open" profile="/usr/sbin/mysqld" name="/sys/devices/system/node/" pid=817 comm="mysqld" requested_mask="r" denied_mask="r" fsuid=0 ouid=0
Nov 12 05:01:03 m3a kernel: [316377.866590] audit: type=1400 audit(1573527663.565:22): apparmor="DENIED" operation="open" profile="/usr/sbin/mysqld" name="/sys/devices/system/node/" pid=819 comm="mysqld" requested_mask="r" denied_mask="r" fsuid=107 ouid=0
Nov 12 05:01:03 m3a mysqld[819]: Initialization of mysqld failed: 0
Nov 12 05:01:03 m3a systemd[1]: mysql.service: Control process exited, code=exited status=1
Nov 12 05:01:03 m3a systemd[1]: mysql.service: Failed with result 'exit-code'.
Nov 12 05:01:03 m3a systemd[1]: Failed to start MySQL Community Server.
Nov 12 05:01:04 m3a systemd[1]: mysql.service: Service hold-off time over, scheduling restart.
Nov 12 05:01:04 m3a kernel: [316378.321822] audit: type=1400 audit(1573527664.021:23): apparmor="DENIED" operation="open" profile="/usr/sbin/mysqld" name="/sys/devices/system/node/" pid=834 comm="mysqld" requested_mask="r" denied_mask="r" fsuid=0 ouid=0                                                                                                                                                                                                     
Nov 12 05:01:04 m3a systemd[1]: mysql.service: Scheduled restart job, restart counter is at 1.
Nov 12 05:01:04 m3a systemd[1]: Stopped MySQL Community Server.
Nov 12 05:01:04 m3a systemd[1]: Starting MySQL Community Server...
Nov 12 05:01:04 m3a kernel: [316378.342296] audit: type=1400 audit(1573527664.041:24): apparmor="DENIED" operation="open" profile="/usr/sbin/mysqld" name="/sys/devices/system/node/" pid=836 comm="mysqld" requested_mask="r" denied_mask="r" fsuid=107 ouid=0                                                                                                                                                                                                   
Nov 12 05:01:04 m3a mysqld[836]: Initialization of mysqld failed: 0
Nov 12 05:01:04 m3a systemd[1]: mysql.service: Control process exited, code=exited status=1
Nov 12 05:01:04 m3a systemd[1]: mysql.service: Failed with result 'exit-code'.
Nov 12 05:01:04 m3a systemd[1]: Failed to start MySQL Community Server.
Nov 12 05:01:04 m3a systemd[1]: mysql.service: Service hold-off time over, scheduling restart.
Nov 12 05:01:04 m3a systemd[1]: mysql.service: Scheduled restart job, restart counter is at 2.
Nov 12 05:01:04 m3a kernel: [316378.823720] audit: type=1400 audit(1573527664.525:25): apparmor="DENIED" operation="open" profile="/usr/sbin/mysqld" name="/sys/devices/system/node/" pid=847 comm="mysqld" requested_mask="r" denied_mask="r" fsuid=0 ouid=0                                                                                                                                                                                                     
Nov 12 05:01:04 m3a systemd[1]: Stopped MySQL Community Server.
Nov 12 05:01:04 m3a systemd[1]: Starting MySQL Community Server...
Nov 12 05:01:04 m3a kernel: [316378.845412] audit: type=1400 audit(1573527664.545:26): apparmor="DENIED" operation="open" profile="/usr/sbin/mysqld" name="/sys/devices/system/node/" pid=849 comm="mysqld" requested_mask="r" denied_mask="r" fsuid=107 ouid=0                                                                                                                                                                                                   
Nov 12 05:01:04 m3a mysqld[849]: Initialization of mysqld failed: 0
Nov 12 05:01:04 m3a systemd[1]: mysql.service: Control process exited, code=exited status=1
Nov 12 05:01:04 m3a systemd[1]: mysql.service: Failed with result 'exit-code'.
Nov 12 05:01:04 m3a systemd[1]: Failed to start MySQL Community Server.
Nov 12 05:01:05 m3a systemd[1]: mysql.service: Service hold-off time over, scheduling restart.
Nov 12 05:01:05 m3a systemd[1]: mysql.service: Scheduled restart job, restart counter is at 3.
Nov 12 05:01:05 m3a systemd[1]: Stopped MySQL Community Server.
Nov 12 05:01:05 m3a systemd[1]: Starting MySQL Community Server...
Nov 12 05:01:05 m3a kernel: [316379.324082] audit: type=1400 audit(1573527665.025:27): apparmor="DENIED" operation="open" profile="/usr/sbin/mysqld" name="/sys/devices/system/node/" pid=861 comm="mysqld" requested_mask="r" denied_mask="r" fsuid=0 ouid=0                                                                                                                                                                                                     
Nov 12 05:01:05 m3a kernel: [316379.344849] audit: type=1400 audit(1573527665.045:28): apparmor="DENIED" operation="open" profile="/usr/sbin/mysqld" name="/sys/devices/system/node/" pid=863 comm="mysqld" requested_mask="r" denied_mask="r" fsuid=107 ouid=0
Nov 12 05:01:05 m3a mysqld[863]: Initialization of mysqld failed: 0
Nov 12 05:01:05 m3a systemd[1]: mysql.service: Control process exited, code=exited status=1
Nov 12 05:01:05 m3a systemd[1]: mysql.service: Failed with result 'exit-code'.
Nov 12 05:01:05 m3a systemd[1]: Failed to start MySQL Community Server.
Nov 12 05:01:05 m3a systemd[1]: mysql.service: Service hold-off time over, scheduling restart.
Nov 12 05:01:05 m3a systemd[1]: mysql.service: Scheduled restart job, restart counter is at 4.
Nov 12 05:01:05 m3a systemd[1]: Stopped MySQL Community Server.
Nov 12 05:01:05 m3a systemd[1]: Starting MySQL Community Server...
Nov 12 05:01:05 m3a kernel: [316379.824323] audit: type=1400 audit(1573527665.525:29): apparmor="DENIED" operation="open" profile="/usr/sbin/mysqld" name="/sys/devices/system/node/" pid=874 comm="mysqld" requested_mask="r" denied_mask="r" fsuid=0 ouid=0
Nov 12 05:01:05 m3a kernel: [316379.845477] audit: type=1400 audit(1573527665.545:30): apparmor="DENIED" operation="open" profile="/usr/sbin/mysqld" name="/sys/devices/system/node/" pid=876 comm="mysqld" requested_mask="r" denied_mask="r" fsuid=107 ouid=0
Nov 12 05:01:05 m3a mysqld[876]: Initialization of mysqld failed: 0
Nov 12 05:01:05 m3a systemd[1]: mysql.service: Control process exited, code=exited status=1
Nov 12 05:01:05 m3a systemd[1]: mysql.service: Failed with result 'exit-code'.
Nov 12 05:01:05 m3a systemd[1]: Failed to start MySQL Community Server.
Nov 12 05:01:06 m3a systemd[1]: mysql.service: Service hold-off time over, scheduling restart.
Nov 12 05:01:06 m3a systemd[1]: mysql.service: Scheduled restart job, restart counter is at 5.
Nov 12 05:01:06 m3a systemd[1]: Stopped MySQL Community Server.
Nov 12 05:01:06 m3a systemd[1]: mysql.service: Start request repeated too quickly.
Nov 12 05:01:06 m3a systemd[1]: mysql.service: Failed with result 'exit-code'.
Nov 12 05:01:06 m3a systemd[1]: Failed to start MySQL Community Server.


---

### Post by SeijiSensei on 2019-11-12
First thing I'd check is the permissions on the directory /var/lib/mysql. The directory and its contents should all be owned by user mysql and group mysql.

---

### Post by marchello_lippi2 on 2019-11-12
> **SeijiSensei said:**
> First thing I'd check is the permissions on the directory /var/lib/mysql. The directory and its contents should all be owned by user mysql and group mysql.
Thanks, applied 
```
sudo chown -R mysql:mysql /var/lib/mysql
```
Will see in couple of days if it will be enough.
Though found another post reg. this issue: 
[https://support.plesk.com/hc/en-us/articles/360004185293-Unable-to-start-MySQL-on-Ubuntu-AVC-apparmor-DENIED-operation-open-](https://support.plesk.com/hc/en-us/articles/360004185293-Unable-to-start-MySQL-on-Ubuntu-AVC-apparmor-DENIED-operation-open-)
(just FYI).

---

### Post by SeijiSensei on 2019-11-12
Did the server start after you changed the permissions? Or do you still get

> Nov 12 05:01:05 m3a mysqld[876]: Initialization of mysqld failed:

There's also an AppArmor problem.  

> Nov 12 05:01:05 m3a kernel: [316379.824323] audit: type=1400 audit(1573527665.525:29): apparmor="DENIED" operation="open" profile="/usr/sbin/mysqld" name="/sys/devices/system/node/" pid=874 comm="mysqld" requested_mask="r" denied_mask="r" fsuid=0 ouid=0

Are you using a version from the repositories or one from some other source?  If the latter, it may not have the required AppArmor markings.  Looks like you can disable AppArmor monitoring of an application by following this method: [https://help.ubuntu.com/community/AppArmor#Disable_one_profile](https://help.ubuntu.com/community/AppArmor#Disable_one_profile)

---

### Post by marchello_lippi2 on 2019-11-12
> **SeijiSensei said:**
> Did the server start after you changed the permissions?
No, it started after I did ```
sudo reboot
```
> Are you using a version from the repositories
Yes, it's from the repositories.
It happens occasionally after ```
sudo /etc/init.d/mysql stop; sudo /etc/init.d/mysql start
``` (but not every time). Thus I will observate it and will update here if it still fails to start in couple of days (and will try to apply AppArmor fix etc).
Thanks!

---

### Post by marchello_lippi2 on 2019-11-14
Ok, it happened again today. 
I added lines below into [FONT=monospace][COLOR=#000000]/etc/apparmor.d/usr.sbin.mysqld and now [/COLOR][/FONT][FONT=monospace][COLOR=#000000]journalctl -xe doesn't say anything about apparmor. But mysql still couldn't start until I rebooted machine... [/COLOR]
[/FONT]> [FONT=monospace][COLOR=#000000]  capability dac_read_search,[/COLOR]
  /proc/*/status r,
  @{PROC}/@{pid}/status r,
  /sys/devices/system/node/ r,
  /sys/devices/system/node/node*/meminfo r,
  /sys/devices/system/node/*/* r,
  /sys/devices/system/node/* r,
[/FONT]

---

### Post by marchello_lippi2 on 2019-11-14
Disabled apparmor profile for mysql
> 
[FONT=monospace][COLOR=#000000]$ sudo ln -s /etc/apparmor.d/usr.sbin.mysqld /etc/apparmor.d/disable/[/COLOR]
[COLOR=#000000]$ sudo apparmor_parser -R /etc/apparmor.d/usr.sbin.mysqld[/COLOR]
[/FONT]
Restarted mysql (successfully). Will see in couple of days if it helped.

---

### Post by marchello_lippi2 on 2019-11-18
So far so good, though waiting more to confirm.

---

### Post by marchello_lippi2 on 2019-11-19
Happened again. But this time I just can't trace it. 

Just ran > [FONT=monospace][COLOR=#000000]sudo /etc/init.d/mysql start[/COLOR][/FONT] and it started successfully without machine reboot.

---

### Post by marchello_lippi2 on 2019-11-19
Added below crontab record under root:
> 9 * * * * bash -c "sleep 10; if pgrep mysql; then exit; else /etc/init.d/mysql start; fi" > /dev/null

Will see in couple of days if it helped.

---

### Post by marchello_lippi2 on 2019-12-28
It still happens. 

Crontab workaround: 
> [FONT=monospace][COLOR=#000000]5 * * * * bash -c "sleep 10; if pgrep mysql; then exit; else /etc/init.d/mysql start; fi" > /dev/null[/COLOR]
7 * * * * bash -c "sleep 10; if pgrep mysql; then exit; else /sbin/reboot; fi" > /dev/null
[/FONT]

See my latest logs below:
>  ([COLOR=#000000][FONT=monospace]systemctl status mysql.service[/FONT][/COLOR])
&#9679; mysql.service - MySQL Community Server
   Loaded: loaded (/lib/systemd/system/mysql.service; enabled; vendor preset: enabled)
   Active: failed (Result: exit-code) since Sat 2019-12-28 08:01:14 EET; 1min 47s ago
  Process: 2526 ExecStart=/usr/sbin/mysqld --daemonize --pid-file=/run/mysqld/mysqld.pid (code=exited, status=1/FAILURE)
  Process: 2517 ExecStartPre=/usr/share/mysql/mysql-systemd-start pre (code=exited, status=0/SUCCESS)
 Main PID: 801 (code=killed, signal=KILL)


Dec 28 08:01:14 m3a.somedomain.com systemd[1]: mysql.service: Service hold-off time over, scheduling restart.
Dec 28 08:01:14 m3a.somedomain.com systemd[1]: mysql.service: Scheduled restart job, restart counter is at 5.
Dec 28 08:01:14 m3a.somedomain.com systemd[1]: Stopped MySQL Community Server.
Dec 28 08:01:14 m3a.somedomain.com systemd[1]: mysql.service: Start request repeated too quickly.
Dec 28 08:01:14 m3a.somedomain.com systemd[1]: mysql.service: Failed with result 'exit-code'.
Dec 28 08:01:14 m3a.somedomain.com systemd[1]: Failed to start MySQL Community Server.


Please see my [COLOR=#333333][FONT=Consolas]journalctl -xe[/FONT][/COLOR] here: [https://pastebin.com/Sqjjedk2](https://pastebin.com/Sqjjedk2) (too big to post here).
Please also see my /var/log/mysql/error.log here: [https://pastebin.com/JTLqWccY](https://pastebin.com/JTLqWccY)
Please advise.

---

### Post by marchello_lippi2 on 2019-12-28
Turns out it's because I have not enough memory and swap is not configured.

[https://medium.com/@jm_c/mysql-crashing-innodb-mmap-bytes-failed-errno-12-64d5b801b2f2](https://medium.com/@jm_c/mysql-crashing-innodb-mmap-bytes-failed-errno-12-64d5b801b2f2)
> 
$ sudo grep -i "mysql" /var/log/syslog


Dec 28 07:31:20 m3a kernel: [767100.510836] [  801]   107   801   404353    45265   733184        0             0 mysqld
Dec 28 07:31:20 m3a kernel: [767100.510978] Out of memory: Kill process 801 (mysqld) score 381 or sacrifice child
Dec 28 07:31:20 m3a kernel: [767100.511040] Killed process 801 (mysqld) total-vm:1617412kB, anon-rss:181060kB, file-rss:0kB, shmem-rss:0kB
Dec 28 07:31:20 m3a kernel: [767100.521099] oom_reaper: reaped process 801 (mysqld), now anon-rss:0kB, file-rss:0kB, shmem-rss:0kB

> $ free -m
              total        used        free      shared  buff/cache   available
Mem:            465         310          34           7         121         135
Swap:             0           0           0


---

### Post by marchello_lippi2 on 2019-12-28
Ok, I followed below manual in order to create swap file:
[https://www.digitalocean.com/community/tutorials/how-to-add-swap-space-on-ubuntu-18-04](https://www.digitalocean.com/community/tutorials/how-to-add-swap-space-on-ubuntu-18-04)
[COLOR=#333333][FONT=&quot]Will see if it helps in couple days or weeks (initial error may occur once a few days or even weeks).[/FONT][/COLOR]

---

