---
title: "Shifted machine  and now cannot access internet"
date: 2014-01-04
forum: General Help
---

### Post by marc14 on 2014-01-04
While trying to get my

1. So we tried to configure a dhcp and it didn't worked. - should work, dhcp is straight forward as we know.
2. We tried to configure a static IP from the file - didn't worked
3. I found some errors in /tc/network/interfaces, we cleaned it up - but didn't helped.
Last thing I tried was to configure static ip from the command line:

sudo ifconfig eth0 192.168.1.4 netmask 255.255.255.0
sudo route add default gw 192.168.1.1 eth0
Now my windows can ping to  8.8.8.8   bout that's it.
I think that by now it should have worked,  As you know we are very limited to debug the issue without any connectivity to the server.

---

### Post by jamesisin on 2014-01-05
You have told us nothing of your network setup nor of the machine in question (it's not even clear if it's running Ubuntu or Windows).  You will want to provide more information about your situation before anyone is likely to be able to help you.

---

