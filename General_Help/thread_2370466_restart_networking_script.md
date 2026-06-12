---
title: "restart networking script"
date: 2017-09-03
forum: General Help
---

### Post by nhk2 on 2017-09-03
Hi all,

I am running 16.04 on a HP Microserver I use it basically just as a NAS for now, I have it automatically set via cron to restart each night at 6am and that works fine so if there are any issues, the reboot every 24 hours means at most it's only going to be down for upto the 24 hours. But a recent problem has appeared that when rebooted at least some times it comes back up with no network access at all and requires a full shut down and restart for it to detect and come back online.

I've searched and tried various scripts posted on the forum but they were all from years and years back and I couldn't get any of them working.

Does anyone know how I can run a script that say runs a ping to a host (like my router ip or google.com or something) and if it gets no reply / is offline I can restart the networking service to force it to come back up? 

even when I look in dmesg it doesn't really explain why the network doesn't come back up some of the times

dmesg |grep enp2s0
[    2.996956] tg3 0000:02:00.0 enp2s0: renamed from eth0
[   31.744235] IPv6: ADDRCONF(NETDEV_UP): enp2s0: link is not ready
[   33.798810] IPv6: ADDRCONF(NETDEV_UP): enp2s0: link is not ready
[   34.668945] tg3 0000:02:00.0 enp2s0: Link is up at 1000 Mbps, full duplex
[   34.668948] tg3 0000:02:00.0 enp2s0: Flow control is off for TX and off for RX
[   34.668970] IPv6: ADDRCONF(NETDEV_CHANGE): enp2s0: link becomes ready

I get the "link is up" after a forced shut down and restart....

---

### Post by untrustytahr on 2017-09-03
Assuming you are using network manager...

```
#!/bin/bash


ping -c4 ip-of-router > /dev/null


if [ $? != 0 ] 
then
    logger "Network connection missing... restarting"
    nmcli connection up *network-name*
fi

```

---

### Post by nhk2 on 2017-09-03
thanks for the reply. I have placed that into /usr/local/bin/check_network

so I just need to run:

```
sudo bash /usr/local/bin/check_network
``` right ?

when i run it, nothing displays... but I guess it will only do something if the network is down? if this works I will place it in cron to run every 10 mins if this will solve the issue

so my cron should look like

[COLOR=#333333][FONT=arial][B]```
*/5 * * * * bash /usr/local/bin/check_network >/dev/null 2>&1
```

doesnt seem to work. I brought the network down and it never came back up at all.[/B][/FONT][/COLOR]

---

### Post by untrustytahr on 2017-09-03
You can put it wherever you would like.  Whatever user is going to run it needs to be able to reach it though.  /usr/local/bin should work.


I would give it a ".sh" extension so I know it's a script as well as making it executable.  That way you will not have to type bash path.  You should be able to run it as your user (though I am running mine on a headless raspberry pi as root- hence no need for output other than logger message).


You may have to install 'logger'.  I'm not sure if that's part of a standard install or if I installed it myself.  It is a utility that will write the message into /var/log/syslog.


*/5 * * * *  /usr/local/bin/check_network.sh >/dev/null 2>&1

Also, be careful if your network name has spaces in it.  You would probably need to escape or quote it (or edit the network name in Network Manager).

---

### Post by nhk2 on 2017-09-03
thanks again for your reply - I tried all of that, once I bring the network down that script doesn't do a single thing to bring it back up. Tried with and without quotes around my network name (which is Wired Network 1 I guess from nmcli.... never used it before)

so I'm right back where I started. There's a whole slew of scripts and posts from years back but none of them contain all the information to actually get it working. The only sure fire way to get the network back up is to force a reboot but that's not so great when I don't know exactly when the network will just not bother to work after an automatic reboot nightly

Ok I did get it working with another method, so far so good I can force the network down and it brings it back up quickly

instead of using ```
[COLOR=#000000][FONT=&quot]nmcli connection up [/FONT][/COLOR][I]network-name
```

[/I]I replaced it with ```
sudo ifconfig enp2s0 up
```

I guess this is the best it will get for me for now.

thanks again

---

