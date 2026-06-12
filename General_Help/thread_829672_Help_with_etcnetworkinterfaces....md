---
title: "Help with /etc/network/interfaces..."
date: 2008-06-15
forum: General Help
---

### Post by hopelessone on 2008-06-15
Hi,

Can someone please help me...

my /etc/network/interfaces file is:

```
auto lo
iface lo inet loopback


iface eth0 inet dhcp

auto eth0
```

If i only have 1 eth0 connection can i just have:

```
auto eth0
iface eth0 inet dhcp
```

Is that OK?

Thanks..

---

### Post by cariboo on 2008-06-15
No you have to have the lo interface too. What is it you are trying to do?

Jim

---

### Post by Rocket2DMn on 2008-06-15
No, many programs listed on the loopback interface (lo) which is your own computer, IP=127.0.0.1, which is also known as *localhost*.

---

### Post by hopelessone on 2008-06-15
I had problems with internet dropping out ...so i changed it to DHCP and seemed to fix it as per here:

[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/209280](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/209280)

I still can't see any uploads in System Monitor or any other network application... per here:

[http://ubuntuforums.org/showthread.php?t=826324](http://ubuntuforums.org/showthread.php?t=826324)

Ahh well...

---

### Post by Rocket2DMn on 2008-06-15
You might be able to get more help in the Networking and Wireless part of the forums - [http://ubuntuforums.org/forumdisplay.php?f=336](http://ubuntuforums.org/forumdisplay.php?f=336)
If you post there, include as much info as possible, including the output of
```
ifconfig
``` along with your screenshots.  It may turn out to be a bug after all, in which case you can search around for others who have had the problem and ask them to confirm your bug report on launchpad.  I will subscribe to your bug report and follow its progress.

---

