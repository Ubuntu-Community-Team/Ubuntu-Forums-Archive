---
title: "Rclone sync and rclone check crashing ubuntu server"
date: 2024-08-14
forum: General Help
---

### Post by atkuzmanov on 2024-08-14
Hope everyone is doing well!


Thanks to everyone in Ubuntu for their amazing work and effort, huge fan, and thanks to anyone willing to help, I really appreciate it, means a lot to me!


I am trying to use rclone to first sync and then check several source and destination directories.


The destinations is an SSD.


I am using rclone to sync around 2TB of data to an SSD.

When I tried to run the rclone check command to the SSD destination the Ubuntu machine froze up and became absolutely non responsive. 
The only way was to do a HARD shut down and start it again.

However lowering the checkers even to 1 did not help (`--checkers=1`).

I played with all parameter/flags I could find which seemed relevant in the rclone documentation, but could not solve the problem.

It looks like when it's running against a faster media such as an SSD it is going over some kind of a limit and it's crashing the Ubuntu machine.

I thought it could be an out of memory issue, however all indicators of the Ubuntu Server machine seem fine.

This is the rclone command which is causing the issue:

The rclone command which is failing:

```

rclone check "$src" "$dest" \

      --checkers=1 \

      --fast-list \

      --multi-thread-streams=0 \

      --buffer-size=0 \

      --one-way \

      --checksum \

      --log-file="$LOG_FILE" \

      --log-level=DEBUG \

      --retries 3 \

      --retries-sleep 3s \

      --progress

```


The full script I use to run the rclone sync and rclone check commands is in pastebin below.

[https://pastebin.com/PxLjAPv5](https://pastebin.com/PxLjAPv5)


---

Ubuntu Server version:

```
ubuntu 24.04 (64 bit)
```

---

Rclone version:

```

rclone --version

rclone v1.67.0

- os/version: ubuntu 24.04 (64 bit)

- os/kernel: 6.8.0-40-generic (x86_64)

- os/type: linux

- os/arch: amd64

- go/version: go1.22.4

- go/linking: static

- go/tags: none

```

---

Rclone config:

[https://pastebin.com/FVWG21Ab](https://pastebin.com/FVWG21Ab)

---

Here are some logs in pastebin:


The log files was more than 90MB, I had to cut out the mundane output from the sync and check to fit the log in pastebin's limits.


But yeah kind of just cuts of while the check is going, the last part of the log is genuine and has not been cut down to fit in pastebin.


[https://pastebin.com/HRpim1yX](https://pastebin.com/HRpim1yX)


This log is a bit more different as it has some weird symbols in the end:


This is the latest log, for some reason it's not showing in full in pastebin unless you click on raw to view it in it's entirety:


[https://pastebin.com/aA0ERkmu](https://pastebin.com/aA0ERkmu)


The log files from the rclone sync or rclone check commands don't have anything which seems to point to any issue.

When the crash happens, the log file just stops at the point of the file which it was currently processing.

---

Its a brand new SSD and I did a SMART test on the SSD and all seems good:

```

sudo smartctl -H /dev/sdc

[sudo] password for usertemp:

smartctl 7.4 2023-08-01 r5530 [x86_64-linux-6.8.0-40-generic] (local build)

Copyright (C) 2002-23, Bruce Allen, Christian Franke, www.smartmontools.org


=== START OF READ SMART DATA SECTION ===

SMART overall-health self-assessment test result: PASSED

```

---

The setup:


```
ProxMox PVE 8.2.4
```


All sources are locally mounted `TrueNas Scale` SMB shares.

TrueNas Scale is also another VM running on the same `ProxMox PVE`, as is the `Ubuntu Server` running `Rclone`.


The TrueNas Scale VM exhibits no sign of any load before, after and ruing when the crash happens, just seems to be chugging along not feeling stressed.


The HDDs and SSD are all directly connected to the computer via a `SAS controller`. The SAS controller is exclusively given to the VM running Ubuntu Server and I see no errors on this side.


Some of the shares have normal or larger files, others have loads of small files.


Ubuntu Server VM:

```

- 8 Cores

- 8GB RAM

```

TrueNas Scale VM:

```

- 4 Cores

- 22GB RAM

- 2 x 6TB NAS HDDs 5400RPM in RAID1

- 1 x 1TB SSD for read cache

```

---

I researched how to debug Ubuntu Server the best I can, and here is what I came up with so far:

Ubuntu Server DEBUG information:

```
sudo cat /var/log/kern.log | grep error
```

[https://pastebin.com/S5VS61Tx](https://pastebin.com/S5VS61Tx)


```
sudo cat /var/log/syslog | grep error
```

[https://pastebin.com/kM3jxVwb](https://pastebin.com/kM3jxVwb)

---

It seems like it's not rclone that is freezing the OS, but something related to I/O reading/writing large amounts of data, but I don't know how to debug it.


I even tried using `ionice -c2 -n7 nice -n 10 rclone check` to reduce the priority of the rclone command to try and throttle the read/write ops, but no joy.


When the crash of the Ubuntu Server VM happens it becomes absolutely non responsive, the guest agent stops running, I cannot SSH into the machine. I also cannot shutdown the machine. Only issuing `STOP` to the VM works in shutting it down, or shutting down the whole ProxMox PVE node, to try and do a more graceful of the VM itself.

I just want it to complete successfully.


I am going crazy trying to figure out what am I doing wrong.


Any help in debugging and fixing this is appreciated!

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=294085&stc=1[/IMG][IMG]https://ubuntuforums.org/attachment.php?attachmentid=294086&stc=1[/IMG][IMG]https://ubuntuforums.org/attachment.php?attachmentid=294087&stc=1[/IMG][IMG]https://ubuntuforums.org/attachment.php?attachmentid=294088&stc=1[/IMG][IMG]https://ubuntuforums.org/attachment.php?attachmentid=294089&stc=1[/IMG][IMG]https://ubuntuforums.org/attachment.php?attachmentid=294086&stc=1[/IMG]

[IMG]https://i.sstatic.net/2qumr5M6.png[/IMG]

---

### Post by currentshaft on 2024-08-14
?

---

### Post by atkuzmanov on 2024-08-15
Hi and thank you for your reply.
I want to use rclone as I want to use it's multithreading capabilities.
I will re-write the script to use rsync and give it a try when I get some time and see if I can reproduce it.
But for now it just looks like it can't handle something I/O or bandwidth related or something...

---

### Post by atkuzmanov on 2024-08-18
> **currentshaft said:**
> Can you reproduce the issue with another program like rsync?

Hi, and thank you for your reply!

I re-wrote the script to use **rsync** and it did not crash.

However I think it's not a problem with **rclone**. I have posted over at the **rclone forum** and the folks there have helped me debug **rclone** and, so far, it does not seem to be an rclone issue.

When it ran with **rsync** it did not reach any high bandwidth throughput, which is I guess to the non-multithreaded nature of **rsync**, it also ran slower, so it did not seem to push something to the limit, something related to I/O reading/writing large amounts of data at a very high speed/rate.

 I do want to be able to use  **rclone** because of it's more advanced features, not just multithreading but encoding, SMB support etc...

I just want to find out where the issue is?

---

### Post by currentshaft on 2024-08-18
<

---

### Post by atkuzmanov on 2024-08-20
> 
currentshaft 	 	 		[INDENT] 			 				Re: Rclone sync and rclone check crashing ubuntu server
 			 			I don't use rclone, but if I wanted to speed up rsync, I would try it  with xargs or parallel (found in the moreutils package). 		[/INDENT] 	


I tried **parallel** to begin with, but still got crashes, that's why I switched to **rclone** to try and use it's flags to throttle and stop the crashes.

---

