---
title: "Upstart (nodejs) + cron = not working"
date: 2014-06-10
forum: General Help
---

### Post by tommy802 on 2014-06-10
Hello, 

I am using 64 bit version of Ubuntu 12.04.4 LTS with NodeJS v0.10.28.

I created an Upstart script to restart my nodejs application once the server or node have been rebooted: 

```

#!upstart
description "Nodejs Appstarter"

start on runlevel [2345]
stop on shutdown

# if node app or server have been crashed, automatically restarting it via respawn:
respawn

script
    export HOME="/home/wbs"
    echo $$ > /var/run/node_app.pid
    cd /home/wbs/node_app
    exec /usr/local/bin/node node_app.js >> /var/log/node_app.log 2>&1
end script

pre-start script
       echo "[`date -u +%Y-%m-%dT%T.%3NZ`] (sys) Starting" >> /var/log/node_app.log
end script

pre-stop script
    rm /var/run/node_app.pid
    echo "[`date -u +%Y-%m-%dT%T.%3NZ`] (sys) Stopping" >> /var/log//node_app.log
end script

post-start script
    echo "node app has been (re)started by upstart!" >>/var/log//node_app.log
end script

```

I saved this upstart file in **node_app.conf** in **/etc/init**

This upstart script works fine. However, for the debugging purpose of the node application, I need to restart my node application every hour.

So I created this simple shellscript : 



```
#!/bin/bash
service node_app restart

```

I put this shellscript in [B]/etc/cron.hourly
[/B]
Unfortunately, cron doesn't restart my node application hourly.


Can anyone tell me  why doesn't it work as expected ? Where is my mistake ?


Thanks in advance !!!

---

