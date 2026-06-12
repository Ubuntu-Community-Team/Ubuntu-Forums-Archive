---
title: "Need a bandwidth monitoring tool ..."
date: 2008-03-10
forum: General Help
---

### Post by vikrant82 on 2008-03-10
Okay, I have used a few like bandwidthd, darkstat, bmon. But problem with all of these is they reset their data on every reboot (at least in their default configurations).

I mean I should be able to get my stats for this month and the data should persist across reboots.

---

### Post by justleen on 2008-03-10
you could use [iptables]("http://www.linux.com/articles/50649") for your stats?

---

### Post by vikrant82 on 2008-03-10
Again as the link suggests, It wont possibly do months, weeks.

Someone suggested [vnstat]("http://www.cyberciti.biz/tips/keeping-a-log-of-daily-network-traffic-for-adsl-or-dedicated-remote-linux-box.html") in comments, that seems to be what I need. :)

---

### Post by vikrant82 on 2008-03-10
> Vnstat has problems associated with it. When an interface is shutdown and brought up after sometime, and vnstat info update for the interface, it adds huge number of downloads and uploads for the interface in its db.

The solution mentioned is -r , > Reset the internal counters in the  database  for  the  selected nterface. Use this if the interface goes down and back up, otherwise that  interface  will  get  some extra  traffic  to  its database.

Hmmmmm ....

---

### Post by vikrant82 on 2008-03-10
> If you reboot the machine or remove the iptables kernel modules, you'll lose all of your packet and byte counters. if these counters are to be used for billing purposes, you will want to make backups of the running counters, and in the event of a reboot, restore the counters rather than starting from zero.

The iptables package comes with two programs that aid in this: iptables-save and iptables-restore. Both programs need to be told to explicitly use the packet and byte counters during backup and restore using the -c command line option.

Hmmm... again the data doesn't persist across reboots. So where would the iptables-save scripts go -  rc6.d ? (and rc0.d ?)

Hmmm, I am still not loving it ;)

---

### Post by phrawzty on 2008-03-10
> **vikrant82 said:**
> Hmmm... again the data doesn't persist across reboots. So where would the iptables-save scripts go -  rc6.d ? (and rc0.d ?)

Hmmm, I am still not loving it ;)

Using iptables-save is pretty straightforward.  To save the data (prior to reboot, for example) :
```
iptables-save -c > /var/tmp/iptables-backup.txt
```

And to restore it (after a reboot, for example) :
```
iptables-restore -c < /var/tmp/iptables-backup.txt
```

You could very easily integrate this into your system.  The "proper" way would be to write a sort of init script, then link it to the runtimes (as you've alluded to above).  A quick and dirty alternative would be to simply add the appropriate save and restore lines to /etc/rc.local and /etc/init.d/reboot respectively.

---

### Post by justleen on 2008-03-10
> **phrawzty said:**
> Using iptables-save is pretty straightforward.  To save the data (prior to reboot, for example) :
```
iptables-save -c > /var/tmp/iptables-backup.txt
```

And to restore it (after a reboot, for example) :
```
iptables-restore -c < /var/tmp/iptables-backup.txt
```

You could very easily integrate this into your system.  The "proper" way would be to write a sort of init script, then link it to the runtimes (as you've alluded to above).  A quick and dirty alternative would be to simply add the appropriate save and restore lines to /etc/rc.local and /etc/init.d/reboot respectively.


quick and dirty other option: add your script to /etc/profile. It will then ne initialized @login.. This should work, unless you need to monitor your bandwitdh with no users logged on.

---

