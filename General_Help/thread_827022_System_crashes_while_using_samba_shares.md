---
title: "System crashes while using samba shares"
date: 2008-06-12
forum: General Help
---

### Post by Kuddel73 on 2008-06-12
Hi!

I've the following problem:

I have a Homeserver (old HP epc 42 with 1GB Ram and a WDC 320 GB HDD) which runs under XUbuntu 8.04. Since a week or so I have problems with system crashes. Before that the machine was running fine 24/7 since several months.

The crashes always and (so far?) only happen when I am trying to download a lot of data over the LAN onto one of my windows machines (Vista). For example Files > 10GB (backups). 

This part of the syslog caught my eye:

> ObiwanKenobi kernel: [   34.341412] PM: Checking swsusp image.
ObiwanKenobi kernel: [   34.341734] PM: Resume from disk failed.
ObiwanKenobi kernel: [   34.380285] EXT3-fs: INFO: recovery required on readonly filesystem.
ObiwanKenobi kernel: [   34.380294] EXT3-fs: write access will be enabled during recovery.
ObiwanKenobi kernel: [   34.802135] kjournald starting.  Commit interval 5 seconds
ObiwanKenobi kernel: [   34.802181] EXT3-fs: sda1: orphan cleanup on readonly fs
ObiwanKenobi kernel: [   34.802194] ext3_orphan_cleanup: deleting unreferenced inode 868382
ObiwanKenobi kernel: [   34.802246] ext3_orphan_cleanup: deleting unreferenced inode 868365
ObiwanKenobi kernel: [   34.802257] ext3_orphan_cleanup: deleting unreferenced inode 868364
ObiwanKenobi kernel: [   34.802268] ext3_orphan_cleanup: deleting unreferenced inode 868363
ObiwanKenobi kernel: [   34.802278] ext3_orphan_cleanup: deleting unreferenced inode 868362
ObiwanKenobi kernel: [   34.802288] ext3_orphan_cleanup: deleting unreferenced inode 868361
ObiwanKenobi kernel: [   34.802296] EXT3-fs: sda1: 6 orphan inodes deleted
ObiwanKenobi kernel: [   34.802299] EXT3-fs: recovery complete.
ObiwanKenobi kernel: [   34.804306] EXT3-fs: mounted filesystem with ordered data mode.


So I ran the s.m.a.r.t. tools as well as some s.m.a.r.t. tests and avery thing seems to be fine. no errors, no problems. Only the HDD temperature seems to be somehow high (51 deg Celsius in idle - about 30 deg outside - but the HDD specs show operating temps of up to 65 deg.)

I know it looks like a hardware failure but what bugs me is the fact that this only happens when I am using the samba server to up- or download data. When the machine is working "locally" on its HDD everything seems to be fine.

Might this be a problem with the network adapter which results in the system freeze?

Any help is very much appreciated. Let me know what other system or log information to post... 


Thanks a lot,
Kuddel73

---

### Post by Kuddel73 on 2008-06-12
I also found a couple of samba errors in my syslog but I'm not sure what those exactly tell me and if these are related to my problem because they appeared not immediately before the crashes:

> 
ObiwanKenobi smbd[5213]: [2008/06/11 18:36:16, 0] lib/util_sock.c:get_peer_addr(1232) 
ObiwanKenobi smbd[5213]:   getpeername failed. Error was Transport endpoint is not connected 
ObiwanKenobi smbd[6300]: [2008/06/11 18:36:16, 0] lib/util_sock.c:get_peer_addr(1232) 
ObiwanKenobi smbd[6300]:   getpeername failed. Error was Transport endpoint is not connected 
ObiwanKenobi smbd[6300]: [2008/06/11 18:36:16, 0] lib/util_sock.c:get_peer_addr(1232) 
ObiwanKenobi smbd[6300]:   getpeername failed. Error was Transport endpoint is not connected 
ObiwanKenobi smbd[6300]: [2008/06/11 18:36:16, 0] lib/access.c:check_access(327) 
ObiwanKenobi smbd[6300]: [2008/06/11 18:36:16, 0] lib/util_sock.c:get_peer_addr(1232) 
ObiwanKenobi smbd[6300]:   getpeername failed. Error was Transport endpoint is not connected 
ObiwanKenobi smbd[6300]:   Denied connection from  (0.0.0.0) 
ObiwanKenobi smbd[6300]: [2008/06/11 18:36:16, 0] lib/util_sock.c:get_peer_addr(1232) 
ObiwanKenobi smbd[6300]:   getpeername failed. Error was Transport endpoint is not connected 
ObiwanKenobi smbd[6300]:   Connection denied from 0.0.0.0 
ObiwanKenobi smbd[6300]: [2008/06/11 18:36:16, 0] lib/util_sock.c:write_data(562) 
ObiwanKenobi smbd[6300]:   write_data: write failure in writing to client 0.0.0.0. Error Connection reset by peer 
ObiwanKenobi smbd[6300]: [2008/06/11 18:36:16, 0] lib/util_sock.c:send_smb(769) 
ObiwanKenobi smbd[6300]:   Error writing 5 bytes to client. -1. (Connection reset by peer)

ObiwanKenobi smbd[6371]: [2008/06/11 21:53:20, 0] lib/util_sock.c:read_data(534) 
ObiwanKenobi smbd[6371]:   read_data: read failure for 4 bytes to client 192.168.1.101. Error = No route to host


ObiwanKenobi smbd[7808]: [2008/06/12 06:03:57, 0] lib/util_sock.c:write_data(562) 
ObiwanKenobi smbd[7808]:   write_data: write failure in writing to client 192.168.1.101. Error Connection reset by peer 
ObiwanKenobi smbd[7808]: [2008/06/12 06:03:57, 0] lib/util_sock.c:send_smb(769) 
ObiwanKenobi smbd[7808]:   Error writing 4 bytes to client. -1. (Connection reset by peer)

ObiwanKenobi smbd[7809]: [2008/06/12 06:27:02, 0] lib/util_sock.c:read_data(534) 
ObiwanKenobi smbd[7809]:   read_data: read failure for 4 bytes to client 192.168.1.101. Error = No route to host 


---

