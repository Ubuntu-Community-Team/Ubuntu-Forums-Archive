---
title: "systemd pid file issues"
date: 2016-04-25
forum: General Help
---

### Post by ben-vectorferret on 2016-04-25
If I use this, the pid file isn't being written. Running the service as root works, but that is not desirable for obvious reasons. I have tried everything I can think of, even creating the pid file in the user's home instead of /var/run but even there the file is never created.

```
[Unit]
Description=Calibre Service
After=network.target

[Service]
Type=forking
User=calibre
Group=calibre
RuntimeDirectory=calibre
RuntimeDirectoryMode=777
PIDFile=/var/run/calibre/calibre-server.pid
ExecStart=/usr/bin/calibre-server \
        --daemonize \
        --max-cover=600x800 \
        --max-opds-items=30 \
        --max-opds-ungrouped-items=100 \
        --username=calibre \
        --port=8080 \
        --url-prefix /books \
        --pidfile=/var/run/calibre/calibre-server.pid \
        --with-library=/pub/Books

[Install]
WantedBy=multi-user.target
```

---

### Post by dom134 on 2016-05-10
Hello there, I think I had this a few days ago, where I could not find the pid file.

I was spending ages and think I eventually ran:

> calibre-server --with-library ~/home

This did seem to work, and then I used systemd to run it automatically on start
> sudo nano /lib/systemd/system/calibre.service

> sudo systemctl enable calibre.service

Now to sort out my reverse proxy issues...

---

### Post by dom134 on 2016-05-30
Hello Ben-vectorferret

I do not think I helped you at all with my last post; I have just reread your post and I am having the same issues as you!  I was running as root and I have tried to create a user/group as you did, but my calibre-service is not starting due to PID write permissions.
I want to do this so that I can access the logfiles for fail2ban.

Did you manage to find a solution?

---

