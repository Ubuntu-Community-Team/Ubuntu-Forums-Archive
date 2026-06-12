---
title: "unity ssh bash intermittently freeze when accessing samba cifs shared folders"
date: 2016-07-06
forum: General Help
---

### Post by mike4ubuntu on 2016-07-06
Has anybody else noticed that on occasions unity, bash, and ssh freeze when you issue some kind of bash command (e.g. ls) on a folder that is mounted with Samba CIFS.  It appears that there is some kind of File System issue.  Rebooting seems to fix the problem, but many times the only way to get it to reboot is to hard reset the box since when it freezes there's no way of issuing a reboot command.  Not only does the server freeze where the initial command (ls -Fals /share) was executed, but if I try to ssh into the server from another machine, it will freeze as well as soon as it logs in.  This is happening on a server that is running 14.04.  the CIFS mount is on a hardware RAID array.

I see a lot of these messages in the /var/log/syslog
```

Jun 27 22:10:41 lic1 kernel: [2588674.770711] CIFS VFS: Server 10.1.10.10 has not responded in 120 seconds. Reconnecting...

```

It doesn't appear to be a network issue since all of the basic services like Apache web server and other network related services all still seem to work.  It seems strictly related to CIFS.  Even ssh seems to work until I get to the bash shell which then hangs.

---

### Post by TheFu on 2016-07-06
If the **PATH** includes anything on network storage, it can take a few seconds to work through all the possible solutions to **tab-completion** or **bash-completion** modules.  Plus CIFS isn't exactly known for high performance or having many options.  "Hardware RAID array" can mean anything from $80 to $8M.  

From a Linux system, it is always best to mount remote storage using NFS.  Just sayin'.

So - if you remove bash-completion and prune the PATH to ensure nothing on network storage is used, I suspect it will speed up again.  Oh ... and don't have '.' in the PATH either.

I've worked with some people having disconnects which were traced back to firewall rules on routers too.  Outbound worked fine between 2 buildings, but storage protocols need 2-way communications, so the inbound firewall rules needed to allow the storage protocol as well.

---

### Post by mike4ubuntu on 2016-07-12
yeah, it actually seems intermittent.  in fact, most of the time it's ok, the tab-completion/bash-completion works just fine.  it normally works even with '.' in the path.  If the problem was related firewall rules, it would happen all of the time.  I'm beginning to suspect that CIFS/samba has some kind of memory leak bug, because it seems that if I reboot the share file server often, it happens much less or not at all.  I also have to say that the size of the shared files is very large, 10+ TB (Terra bytes).  Maybe Samba doesn't easily handle that size.  Also, there are many small files and very large files mixed in folders everywhere in the directory tree.  However, I have to reiterate that it is intermittent.  Most of the time it works just fine with relatively good performance, but when it freezes it will stay frozen anywhere from 10 minutes to 3 hours or more before unfreezing.  If I reboot the server, the CIFS file system will be fine without any problems until the next freeze which can be days or weeks later.  I don't use NFS since I have windows boxes that need to access the share folders, and I have found that windows has less issues with Samba.

Additional specs: I use LSI 3ware 9750 RAID controller cards for the RAID 1-0 array of Seagate 8 TB archive hard drives containing the Samba/CIFS mounting.

---

### Post by mike4ubuntu on 2016-07-12
yeah, it actually seems intermittent.  in fact, most of the time it's ok, the tab-completion/bash-completion works just fine.  it normally works even with '.' in the path.  If the problem was related firewall rules, it would happen all of the time.  I'm beginning to suspect that CIFS/samba has some kind of memory leak bug, because it seems that if I reboot the share file server often, it happens much less or not at all.  I also have to say that the size of the shared files is very large, 10+ TB (Terra bytes).  Maybe Samba doesn't easily handle that size.  Also, there are many small files and very large files mixed in folders everywhere in the directory tree.  However, I have to reiterate that it is intermittent.  Most of the time it works just fine with relatively good performance, but when it freezes it will stay frozen anywhere from 10 minutes to 3 hours or more before unfreezing.  If I reboot the server, the CIFS file system will be fine without any problems until the next freeze which can be days or weeks later.  I don't use NFS since I have windows boxes that need to access the share folders, and I have found that windows has less issues with Samba.

Additional specs: I use LSI 3ware 9750 RAID controller cards for the RAID 1-0 array of Seagate 8 TB archive hard drives containing the Samba/CIFS mounting.

---

### Post by TheFu on 2016-07-12
Ah ... lots and deep directory structures ... there is an option during mount to limit how much discovery is performed. I don't remember it now. Sorry. [https://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/speed.html](https://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/speed.html) probably has it.

Windows really needs samba, but Unix clients should use NFS. Both can be used for the same storage.
Seagate - ah .... how I used to love you (only bought seagate for a long time), but now avoid you like I'd avoid TB, plague, Ebola ... you get the idea.  Certain seagate SATA drives have very high mortality rates. There's a study published quarterly by BackBlaze. [https://www.backblaze.com/blog/hard-drive-reliability-stats-q1-2016/](https://www.backblaze.com/blog/hard-drive-reliability-stats-q1-2016/)  This doesn't apply to their SAS drives, but most people here won't spend for the enterprise disks.

---

