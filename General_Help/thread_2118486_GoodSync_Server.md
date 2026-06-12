---
title: "GoodSync Server"
date: 2013-02-21
forum: General Help
---

### Post by Jay Banks on 2013-02-21
Anyone with any experience with GoodSync Server on Ubuntu?

I finally managed to get it running as a service and starting at startup if I have to reboot. I have one issue and I think it will work if I fix it. I see the server from a Windows client, but I get this error in the client:

gsconnectanyfs cannot create fs instance for: /home/jbanks/nwci-goodsync

I have it set to impersonate me, and I have all rights to this folder because it is my folder.

-=-=-=

This is how I'm starting the server using upstart:

description "GoodSync application"
author "GoodSync"



start on (local-filesystem and net-device-up IFACE=eth0)
start on startup
stop on shutdown

respawn

exec start-stop-daemon --start --chuid 1000 --exec /home/jbanks/Programs/goodsync-release-x86_64/gs-server

-=-=-=

I'm user 1000, and /home/jbanks is my home folder, so it should be able to read/write to the folder.

Any help would be great. If I figure it out, I will post answer for everyone.

---

