---
title: "apache2 privetetemp"
date: 2018-05-01
forum: General Help
---

### Post by pqwoerituytrueiwoq on 2018-05-01
How can i make this change not get undone via updates?
```
chad@Z97Killer:~$ cat /lib/systemd/system/apache2.service
[Unit]
Description=The Apache HTTP Server
After=network.target remote-fs.target nss-lookup.target

[Service]
Type=forking
Environment=APACHE_STARTED_BY_SYSTEMD=true
ExecStart=/usr/sbin/apachectl start
ExecStop=/usr/sbin/apachectl stop
ExecReload=/usr/sbin/apachectl graceful
**PrivateTmp=false**
Restart=on-abort

[Install]
WantedBy=multi-user.target


```

---

### Post by pqwoerituytrueiwoq on 2018-05-04
Here is how to disable it for good:
```
sed 's/PrivateTmp=true/PrivateTmp=true/' /lib/systemd/system/apache2.service | sudo tee /etc/systemd/system/apache2.service
```

---

