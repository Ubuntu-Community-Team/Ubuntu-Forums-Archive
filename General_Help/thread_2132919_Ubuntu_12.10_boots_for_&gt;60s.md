---
title: "Ubuntu 12.10 boots for &gt;60s"
date: 2013-04-06
forum: General Help
---

### Post by kwanylongy on 2013-04-06
Dear all,

I would like to speed the boot time of My Ubuntu 12.10 (which boots for >60s). I found [this post]("http://ubuntuforums.org/showthread.php?t=1976094") and tried the solution at #4:

```

echo "blacklist r8169" | sudo tee /etc/modprobe.d/blacklist-ethernet.conf
gksudo gedit /etc/rc.local

```

But sadly it didn't work. (FYI: The thread owner also found this solution not working originally, but it worked mysteriously after he retried it a month later)

Anyone has any idea how to fix it?

Many many thanks!

kwanylongy

The following is an extract of my dmesg output (which shows that there's a 26s delay):

```
[    0.000000] Initializing cgroup subsys cpuset
[    2.614000] sd 2:0:0:2: [sdd] Attached SCSI removable disk
[    2.614752] sd 2:0:0:3: [sde] Attached SCSI removable disk
[   27.684056] Adding 4192252k swap on /dev/sda5.  Priority:-1 extents:1 across:4192252k 
[   28.303232] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   28.419949] udevd[334]: starting version 175
[   29.269395] lp: driver loaded but no devices found

```

---

### Post by tgalati4 on 2013-04-06
Open a terminal:

```
sudo apt-get install bootchart pybootchartgui
```

Run bootchart and examine the output.  Look for Input/Output (IO) bound processes and see which ones take the longest.  It's possible that one or two daemons are slow to initialize, waiting for the network or other data.

These are old boot charts but they give you a feel for how bootchart works:  [http://www.bootchart.org/samples.html](http://www.bootchart.org/samples.html)

Search the **NewDocs** link below for *bootchart* for additional information on how to run it.

---

### Post by kwanylongy on 2013-04-06
Thanks for your reply, tgalati4

I know bootchart and originally wanted to put it here together with my dmesg, but I had a problem running it last night. Anyway, I have fixed the problem now and here it is.

Regarding to look for the longeset IO processs in my bootchart, I hardly understand the processes listed in bootchart (other than the common applications, such as chrome, pidgn, sorry for my noobs), would you mind taking a look at my bootchart?

Many many thanks,

Carlos

[IMG]https://dl.dropbox.com/u/57345394/asurada-quantal-20130407-1.png[/IMG]

---

