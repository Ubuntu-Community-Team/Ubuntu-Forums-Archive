---
title: "run command after startup and wake up from system-sleep"
date: 2019-03-21
forum: General Help
---

### Post by Martin_Mucha on 2019-03-21
Hi,

I have systemd service to start fancontrol, which looks like this:

```
cat /etc/systemd/system/fancontrol.service


[Unit]
Description=fancontrol service
After=suspend.target hibernate.target hybrid-sleep.target 


[Service]
Type=simple
ExecStart=/usr/sbin/fancontrol


[Install]
WantedBy=suspend.target basic.target hibernate.target hybrid-sleep.target

```

the problem is, that after waking from (hybrid?) sleep, the fancontrol is allegedly running, but fan is stopped, and I have to manually run: `systemctl restart fancontrol`

I tried to install systemd wakeup hook then:

```
sudo cat /lib/systemd/system-sleep/restartFancontrol.sh 
#!/bin/sh
case $1/$2 in
  pre/*)
    exit 0 
    ;;
  post/*)
    systemctl restart fancontrol	  
    exit 0
    ;;
esac

which works, but for some reason, this will also wake up my laptop "without wifi" and it takes around 5 minutes since "something" restarts and I have wifi back, which is not neither convenient nor something I actually want.

Any idea how to restart make fancontrol restart after wakeup?



```

---

