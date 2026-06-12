---
title: "Prevent systemd service from restarting on apt upgrade"
date: 2024-07-02
forum: General Help
---

### Post by joskrieckaart on 2024-07-02
I have a custom service, for which I made a systemd service configuration file. Every time I run "apt-get upgrade" and any package is upgraded, the service is restarted, also when I believe it is not needed. Can I add or change something to the systemd service configuration file to prevent it from restarting every time.

This is the content of the service configuration file:

```

[Unit]                                                                                                  
Description=MyApp
Wants=network.target
After=network.target


[Service]
Type=simple
ExecStart=/usr/bin/java -jar /apps/myapp/MyApp.jar
PIDFile=/apps/myapp/pid/MyApp.pid
User=jos
RemainAfterExit=yes


[Install]
WantedBy=multi-user.target

```

---

### Post by ActionParsnip on 2024-07-02
What is the output of:
```

systemctl status modulenamehere

```

---

### Post by joskrieckaart on 2024-07-02
Here is the output:

```

 myapp.service - MyApp
     Loaded: loaded (;;file://meter/etc/systemd/system/myapp.service/etc/systemd/system/myapp.service;;; enabled; preset: enabled)
     Active: active (running) since Mon 2024-07-01 11:18:53 CEST; 1 day 3h ago
   Main PID: 116267 (java)
      Tasks: 42 (limit: 9313)
     Memory: 2.8G (peak: 3.1G)
        CPU: 36min 43.748s
     CGroup: /system.slice/myapp.service
             &#9492;&#9472;116267 /usr/bin/java -jar /apps/myapp/MyApp.jar

```

---

### Post by joskrieckaart on 2024-07-16
I did some research. I found that needrestart flags the service for restart. It seems to think that /usr/bin/java depends on something that has always changed.
As a workaround, I added "qr(^myapp) => 0," to the overrides in /etc/needrestart/needrestart.conf.

---

