---
title: "azureus unable to download"
date: 2007-10-14
forum: General Help
---

### Post by vsayikiran on 2007-10-14
i am using latest version of azureus . i am behind a proxy server. i have entered that information in options. next i have also run iptables command to allow certain tcp and udp port. still it is not able to dwonload. if somebody had same problems then please share with me. what can i do to download

---

### Post by ExcallibuR on 2008-06-03
yes me too having the same problem can connect the tracker but having problem with peer connection....i hav tried proxychains too bt i'm not sure if the configurations are all rt...

see this...and pl someone tell meh what may be the problem...

ubuntu@ubuntu-desktop:~$ sudo proxychains /usr/bin/azureus
Looking for and picking a preferred Java runtime
Use environment AZUREUS_JAVA to override
Using Java: /usr/lib/jvm/java-6-openjdk/jre/bin/java
[GUI] StartServer ERROR: unable to bind to 127.0.0.1:6880 listening for passed torrent info: Address already in use
StartSocket: passing startup args to already-running Azureus java process listening on [127.0.0.1: 6880]


thnx in advance..

---

### Post by Prospero2006 on 2008-06-03
It depends on what kind of proxy you are behind.
I work at a public school and the network guys only allow traffic to flow in and out on ports 80 and 443.

So, if you are running azureus behind a proxy like that, you'll have to take some extra steps.
Try this:
```

sudo export http_proxy="http://youproxy.address:port"
sudo export https_proxy="http://yourproxy.address:port"


```

That might help.

---

