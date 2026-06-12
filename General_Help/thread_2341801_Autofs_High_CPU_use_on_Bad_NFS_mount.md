---
title: "Autofs High CPU use on Bad NFS mount"
date: 2016-10-31
forum: General Help
---

### Post by EricRanders on 2016-10-31
Hello,
 
 
 I have an Ubuntu 14.04 64 bit server running Bluecherry network video software.  This server uses autofs to mount an NSF share served from a FreeNAS. Everything works perfect until NFS mount is broken. The Ubuntu server locks up and is pretty much unusable at this point. I’ve tried using different  mounting options in autofs without luck.  The Bluecherry software can write to many directories at once but is useless with such a high cpu load due to the broken NFS mount. It will also keep trying to write to the broken mount point. If at all possible I would like autofs to stop trying to mount the NSF share after a few attempts and maybe retry every hour or so. I've read everything I could find and am a loss on how this should be done. Let me thank everyone in advance for any ideas you may have.

---

### Post by TheFu on 2016-11-01
Exactly what options have you tried?  That is where the answer is ... besides having stable NFS storage.

---

### Post by EricRanders on 2016-11-02
I've set tried these options as well as every other option I could think of in /etc/auto.nfs 

NAS        -soft,intr,timeo=5,retrans=5,actimeo=10,retry=5        192.168.1.11:/mnt/vol1

as well as adding --retry=0  --timeout=2 --ghost  flags to /etc/auto.master


FreeNAS is very stable but I can't have any type of failure  NAS, network, or otherwise to take down the server recording the video. In fact we have redundant servers and redundant freeNAS boxes but they will still lock up if any one of the mounts goes bad.

---

### Post by TheFu on 2016-11-02
Did you try those options 1-at-a-time?  
Also, if there are any routers/firewalls between the storage and the servers, check them for settings that are getting in the way of NFS ports.

Have you considered clustered, redundant, storage?  Not certain if that would work for you, but I've been looking at sheepdog recently.

---

### Post by EricRanders on 2016-11-03
I've tried every option in ever way I could think of. Let me clarify everything works perfect. I don't think the FreeNAS server has ever gone off line on it's own only do to power outages and updates ect. This setup has been rock solid. To simulate an outage I tun off NSF on the FreeNAS server to simulate what would happen in the event it failed. The Bluecherry Network video servers have the capability to record in multiple directories and would do so if it were not for the high CPU load due the broken NFS mount.

Sheepdog looks interesting. I will look into it for sure.

---

