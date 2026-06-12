---
title: "Gutsy: Hibernate causes Network Manager to run 100% CPU"
date: 2007-10-22
forum: General Help
---

### Post by garymansell on 2007-10-22
Hi

I have a HP ZD8000 laptop with Gutsy installed and when I boot the machine from hibernation mode the Network Manager consumes 100% cpu and the wireless network does not restart correctly.

Any Ideas

Rgds

Gary

---

### Post by qiemem on 2007-10-22
I have the exact same problem when I come back from suspend.  Network manager does not show up in the System Monitor, but from 'top':
```

PID USER      PR  NI  VIRT  RES  SHR   S  %CPU %MEM    TIME+    COMMAND 
4582 root      15   0 28952 2056 1792 S 84.7   0.4         8:18.73  NetworkManager 

```
Furthermore, this process cannot be killed, or rather I have not been able to.

Wireless card (from lspci):
```
 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
```

I do have a bit of a workaround.  I have found that connecting to a network via the terminal still works in these conditions.  To do so, open a terminal (replace eth1 with whatever your wireless card's name thingy is.  This can be found by entering 'ifconfig' into the terminal):
```

sudo ifconfig eth1 up    // I usually find the wireless card has been turned off, so this turns it back on
iwlist scanning              // This will give you a list of all available wireless networks
sudo iwconfig eth1 essid <wireless network name>    // tells it which network to connect to
sudo dhclient eth1         // Gets an ip address from the network.

```

That usually works for me.  Though this doesn't solve the 100% cpu issue; computer still takes hits from that.

Anyway, if I find anything else I'll let you know.
Anyone have a better solution?

---

### Post by adamonduty on 2007-10-23
I'm having the same problem after suspend. I did a distribution upgrade from edgy.

The CPU issue is very annoying since it causes all the fans to come on on my laptop. Also, networking does not work.

You CAN kill the network manager process by running 

```
$ kill -9 <pid>
```

Networking with Network Manager is pretty useless after that.

I'm running an intel 2200b/g which uses the ipw2200 broadcom module. Maybe we should file a bug report?

---

### Post by rennerc on 2007-10-24
i have a similar problem that NetworkManager does not work at all after resume from hibernate.

this fixes it for me:

```
sudo killall -9 NetworkManager
sudo /etc/dbus-1/event.d/25NetworkManager start
```

---

### Post by rennerc on 2007-10-24
installing hibernate did solve it for me

```
sudo apt-get install hibernate
```

---

### Post by jkyamog on 2007-10-24
I have a similar problem, even using the hibernate package.  I came from a Feisty upgrade.  My laptop is a HP DV6000

My wireless card is a broadcom

02:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 01)

Similar work around is to kill -9 <pid of NetworkManager>, then start NetworkManager.  Maybe we should add a report to launchpad?

---

### Post by huzzak on 2007-11-08
I've been having the same problem on my hp dv5237cl with Gutsy.  It doesn't happen every time, but often enough that it is really annoying.  I've found that running "sudo /etc/init.d/dbus restart" cures the wireless and the cpu running so high, but also stops the battery level indicator from appearing and removes my ability to suspend or hibernate.  I just installed the hibernate package and we'll see if that does anything.

---

### Post by huzzak on 2007-11-08
Aha.  After installing hibernate I can no longer suspend.  This, I suppose, solves the problem, in its own way, but not in a way that makes me happy.  Any ideas about why this is so?

---

### Post by kvpetrov on 2007-11-11
Killing NetworkManager and restarting it does the trick for me... but of course it is very annoying, did anybody report this as a bug?

---

### Post by GroupB on 2007-12-08
Yup, exact same problem for me too.  Very annoying.  It happens about 50% of the time when I fire back up from either "hibernate" or "suspend".  The only thing I am can do to cure it is to do a re-boot.  Good point in the previous post though:  anyone report this yet as a bug?  If not, I guess I will in few days, if their is no response from another user.

---

