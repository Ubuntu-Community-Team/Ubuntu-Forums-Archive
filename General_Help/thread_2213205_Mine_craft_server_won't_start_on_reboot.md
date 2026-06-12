---
title: "Mine craft server won't start on reboot"
date: 2014-03-25
forum: General Help
---

### Post by brotherchris on 2014-03-25
Hello all,

I have been banging my head on this for days now, and decided to get some help. I am trying to get my mine craft server to restart when I reboot. The script just keeps throwing errors. I am running 12.04 server. My script looks like this.

console log

exec start-stop-daemon --stop "stop" --start --chdir /minecraft --chuid minecraft \
        --exec /usr/bin/java -- -Xms1536m -Xmx2048M -jar minecraft_server.jar nogui 2>&1

start on runlevel [2345]
stop on runlevel [^2345]

respawn
respawn limit 20 5

Every time I try to start it, I get this error in the /var log.

root@bcserv:/# tail /var/log/upstart/minecraft-server.log
start-stop-daemon: only one command can be specified
Try 'start-stop-daemon --help' for more information.

I can't figure out what exec is wanting me to do. Any help is appreciated.

Chris

---

