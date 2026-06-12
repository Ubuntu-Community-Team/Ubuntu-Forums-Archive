---
title: "Failed to start The Apache HTTP Server."
date: 2018-06-11
forum: General Help
---

### Post by gysmo.net on 2018-06-11
&#9679; apache2.service - The Apache HTTP Server
   Loaded: loaded (/lib/systemd/system/apache2.service; enabled; vendor preset: enabled)
  Drop-In: /lib/systemd/system/apache2.service.d
           &#9492;&#9472;apache2-systemd.conf
   Active: failed (Result: exit-code) since Mon 2018-06-11 08:06:59 EDT; 43min ago
  Process: 1518 ExecStart=/usr/sbin/apachectl start (code=exited, status=1/FAILURE)

Jun 11 08:06:59 gysmonet-HP-Z800-Workstation apachectl[1518]: AH00558: apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1. Set the 'Se
Jun 11 08:06:59 gysmonet-HP-Z800-Workstation apachectl[1518]: (98)Address already in use: AH00072: make_sock: could not bind to address [::]:80
Jun 11 08:06:59 gysmonet-HP-Z800-Workstation apachectl[1518]: (98)Address already in use: AH00072: make_sock: could not bind to address 0.0.0.0:80
Jun 11 08:06:59 gysmonet-HP-Z800-Workstation apachectl[1518]: no listening sockets available, shutting down
Jun 11 08:06:59 gysmonet-HP-Z800-Workstation apachectl[1518]: AH00015: Unable to open logs
Jun 11 08:06:59 gysmonet-HP-Z800-Workstation apachectl[1518]: Action 'start' failed.
Jun 11 08:06:59 gysmonet-HP-Z800-Workstation apachectl[1518]: The Apache error log may have more information.
Jun 11 08:06:59 gysmonet-HP-Z800-Workstation systemd[1]: apache2.service: Control process exited, code=exited status=1
Jun 11 08:06:59 gysmonet-HP-Z800-Workstation systemd[1]: apache2.service: Failed with result 'exit-code'.
Jun 11 08:06:59 gysmonet-HP-Z800-Workstation systemd[1]: Failed to start The Apache HTTP Server.

am new and using the desktop 18,04 and trying to set a simple working server working back end is it possible
and how to fix this issue

---

### Post by Doug S on 2018-06-11
Is something already using port 80? Check via, and for example:

```
doug@DOUG-64:~$ [COLOR="#FF0000"]sudo netstat -tlnp[/COLOR]
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 0.0.0.0:25              0.0.0.0:*               LISTEN      1568/master
tcp        0      0 127.0.0.1:953           0.0.0.0:*               LISTEN      1294/named
tcp        0      0 0.0.0.0:445             0.0.0.0:*               LISTEN      1137/smbd
tcp        0      0 127.0.0.1:3306          0.0.0.0:*               LISTEN      1343/mysqld
tcp        0      0 0.0.0.0:139             0.0.0.0:*               LISTEN      1137/smbd
[COLOR="#FF0000"]tcp        0      0 0.0.0.0:80              0.0.0.0:*               LISTEN      8646/apache2[/COLOR]
tcp        0      0 192.168.111.1:53        0.0.0.0:*               LISTEN      1294/named
tcp        0      0 173.XXX.XX.X:53         0.0.0.0:*               LISTEN      1294/named
tcp        0      0 127.0.0.1:53            0.0.0.0:*               LISTEN      1294/named
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN      1269/sshd

```

---

### Post by gysmo.net on 2018-06-11
gysmonet@gysmonet-HP-Z800-Workstation:~$ sudo netstat -tlnp
[sudo] password for gysmonet: 
sudo: netstat: command not found
gysmonet@gysmonet-HP-Z800-Workstation:~$

sorry had to leave fr couple hours but again  tried this command and not seem to work

---

