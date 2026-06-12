---
title: "Moving home folder not going to plan"
date: 2013-02-23
forum: General Help
---

### Post by nickdc on 2013-02-23
I've been trying to move my home folder to a separate partition. I've been following the guidance in the Community Docs here:

[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

When I get to the end of Step 3, "Check Copying Worked", I get a whole screed of stuff which I didn't anticipate. 
eg:
nick@nick-build-1:~$ sudo diff -r /home /media/home
[sudo] password for nick: 
Only in /media/home: lost+found
File /home/nick/.cache/gnome-system-monitor.nick.2168612713 is a socket while file /media/home/nick/.cache/gnome-system-monitor.nick.2168612713 is a socket
diff -r /home/nick/.cache/ubuntuone/log/syncdaemon.log /media/home/nick/.cache/ubuntuone/log/syncdaemon.log
37,46d36
< 2013-02-23 13:46:34,291 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'QUEUE_MANAGER'  (queues IDLE  connection 'With User With Network')>; queue: 0; offloaded: 0; hash: 0) ----
< 2013-02-23 14:01:34,419 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'QUEUE_MANAGER'  (queues IDLE  connection 'With User With Network')>; queue: 0; offloaded: 0; hash: 0) ----
< 2013-02-23 14:16:34,369 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'QUEUE_MANAGER'  (queues IDLE  connection 'With User With Network')>; queue: 0; offloaded: 0; hash: 0) ----
< 2013-02-23 14:31:34,339 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'QUEUE_MANAGER'  (queues IDLE  connection 'With User With Network')>; queue: 0; offloaded: 0; hash: 0) ----
< 2013-02-23 14:46:34,318 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'QUEUE_MANAGER'  (queues IDLE  connection 'With User With Network')>; queue: 0; offloaded: 0; hash: 0) ----
< 2013-02-23 15:01:34,433 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'QUEUE_MANAGER'  (queues IDLE  connection 'With User With Network')>; queue: 0; offloaded: 0; hash: 0) ----
< 2013-02-23 15:16:34,347 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'QUEUE_MANAGER'  (queues IDLE  connection 'With User With Network')>; queue: 0; offloaded: 0; hash: 0) ----
< 2013-02-23 15:31:34,285 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'QUEUE_MANAGER'  (queues IDLE  connection 'With User With Network')>; queue: 0; offloaded: 0; hash: 0) ----
< 2013-02-23 15:46:34,278 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'QUEUE_MANAGER'  (queues IDLE  connection 'With User With Network')>; queue: 0; offloaded: 0; hash: 0) ----
< 2013-02-23 16:01:34,285 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'QUEUE_MANAGER'  (queues IDLE  connection 'With User With Network')>; queue: 0; offloaded: 0; hash: 0) ----
diff: /home/nick/.config/autostart/padevchooser.desktop: No such file or directory
diff: /media/home/nick/.config/autostart/padevchooser.desktop: No such file or directory
File /home/nick/.config/gxine/socket is a socket while file /media/home/nick/.config/gxine/socket is a socket

....

I killed it at this point, though I suspect it was still comparing, as there's over 100Gb in my Home folder.

I'd be grateful if someone could interpret this data for me and tell me whether it matters, and how I should proceed.

For info, I'm the only user on this pc so no other user accounts. And I'm using Ubuntu 12.04. (Wanting to move the home folder before upgrading, to make clean installs easier in future.)

Any advice would be much appreciated.

---

