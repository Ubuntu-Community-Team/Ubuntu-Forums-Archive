---
title: "atftpd port help"
date: 2007-10-22
forum: General Help
---

### Post by rosarch on 2007-10-22
I am trying to get mediamvp working with my ubuntu mythtv box. As far as I can make out the mediamvp box connects via tftp on port 69 reboots then make a connection on port 16869 the first connection is okay but the second doesn't appear to be working. I think this is because atftpd is only listening on port 69.

How can I change the config below to also listen on port 16869?


more /etc/default/atftpd
USE_INETD=true
OPTIONS="--daemon --port 69 --tftpd-timeout 300 --retry-timeout 5     --mcast-port 1758 --mcast-addr 239.239.239.0-255 --mcast-ttl 1 --maxthre
ad 100 --verbose=5  /tftpboot"

Thanks in advance for any advice offered.

Cheers
Dave

---

