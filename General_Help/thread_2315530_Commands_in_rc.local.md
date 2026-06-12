---
title: "Commands in rc.local"
date: 2016-02-29
forum: General Help
---

### Post by Alexander_Lilljebj on 2016-02-29
Hello, 
I'm trying to add the following commands to rc.local:
iptables -A OUTPUT -m owner --gid-owner vpnroute \! -o tun0 -j REJECT
and 
-g vpnroute transmission-gtk

This is to force transmission to only use my vpn and then launch it. 
Vpnroute group is present and lc.local is owned by root and can be executed. 
 
Have also tried to start via lxsessions startup manager with no luck. 

Been trying for a couple of days now and it's doing my head in :(

Any help would be greatly appreciated! 
Best regards Alex

Edit: I've also tried to make a script, chmod it and call it from rc.local. The script itself can be run without problems from terminal, however nothing happens at startup.
Then I tried to make a .desktop file to execute the script, put it in /home/username/.config/autostart, didn't work either.
Feels like I'm missing something quite basic/fundamental...

---

### Post by s0urCr34m on 2016-03-05
Have you tried making a script in /etc/network/if-up.d/ ? I'm not saying this is a fix, but it's worth a try.

---

### Post by nerdtron on 2016-03-05
So you made a script already and it runs fine when you run it manually? Why not proceed further and try to add a delay. Also try to run it on crontab instead
I think the problem is that maybe the network is not yet fully connected when the script is run, so you need to set a delay for it to run:
```

#!/bin/bash
## add a sleep of 60 seconds to let the system initialize everything before running the below commands
sleep 60

## after the delay, run commands here::
iptables -A more syntax here


```


Now you can try to call that script on the rc.local file. But I think that this will cause your bootup to wait for 60 seconds. You may want to use crontab instead with the @reboot schedule:
```
@reboot /bin/bash /your/path/to/the/script.sh 
```

---

### Post by springshades on 2016-05-09
I'll answer this in a few places because it's useful information and not terribly easy to find right now. Ubuntu is now using systemd, and rc.local is now considered a service which is turned "off" by default. You can turn rc.local "on" by entering the following command and rebooting:

sudo systemctl enable rc-local.service

---

