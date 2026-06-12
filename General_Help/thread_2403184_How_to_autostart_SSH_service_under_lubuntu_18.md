---
title: "How to autostart SSH service under lubuntu 18?"
date: 2018-10-08
forum: General Help
---

### Post by dawciobiel on 2018-10-08
How to enable autostart for ssh (*openssh**-server*) under lubuntu 18 x64

I installed*openssh**-server* by: 
[COLOR=#000000][FONT=menlo]
# tasksel install openssh-server[/FONT][/COLOR]

After [COLOR=#000000][FONT=menlo]
[/FONT][/COLOR]
```

# service ssh start
# service ssh status


&#9679; ssh.service - OpenBSD Secure Shell server
   Loaded: loaded (/lib/systemd/system/ssh.service; enabled; vendor preset: enabled)
   Active: active (running) since Mon 2018-10-08 17:16:17 CEST; 15s ago
  Process: 1607 ExecStartPre=/usr/sbin/sshd -t (code=exited, status=0/SUCCESS)
 Main PID: 1608 (sshd)
    Tasks: 1 (limit: 4585)
   CGroup: /system.slice/ssh.service
           &#9492;&#9472;1608 /usr/sbin/sshd -D


pa&#378; 08 17:16:17 cerebro systemd[1]: Starting OpenBSD Secure Shell server...
pa&#378; 08 17:16:17 cerebro sshd[1608]: Server listening on 192.168.0.16 port 22222.
pa&#378; 08 17:16:17 cerebro systemd[1]: Started OpenBSD Secure Shell server.


```

So as I can see autostart it's "enable". But after *reboot *I got:

# service ssh status
&#9679; ssh.service - OpenBSD Secure Shell server
   Loaded: loaded (/lib/systemd/system/ssh.service; enabled; vendor preset: enabled)
   Active: inactive (dead)

I even tried

# systemctl enable ssh
Synchronizing state of ssh.service with SysV service script with /lib/systemd/systemd-sysv-install.
Executing: /lib/systemd/systemd-sysv-install enable ssh

or
 # service ssh enable

or even
# update-rc.d ssh enable 2 3 4 5

Still autostart not working.

---

### Post by dawciobiel on 2018-10-09
[COLOR=#000000]# dpkg-reconfigure openssh-server

[/COLOR][COLOR=#000000]# cd /etc/NetworkManager/dispatcher.d/[/COLOR]
[COLOR=#000000]# echo /etc/init.d/ssh restart > ./10ssh[/COLOR]
[COLOR=#000000]# chmod 755 ./10ssh

[/COLOR]# systemctl enable ssh.service

[B]Since now autostart it's working.
[/B]

---

