---
title: "Delay the restart of a Service after Networking has been restored"
date: 2013-02-22
forum: General Help
---

### Post by gumsh on 2013-02-22
I am using Ubuntu 12.10 on my Media Center PC running XBMC as frontend. In Addition i use it as a Download Manager using pyload, so i can download files using the full bandwidth of my cable connection and having it connected via ethernet and directly extract to my file server. 
I usually send the system to suspend when i'm not using it which is working fine for everything except pyload. Pyload needs a restart after "supend" in order to maintain login information on hosters and stuff so i insertet a "service restart" into one of my sleep.d scripts.

Now the problem is that the service is started so fast, that it is started before the Network connection is active again. When i add a "sleep 10" delays the start all right, but it seems to delay establishing the connection as well.

This is driving me crazy since i have to manually restart the service after resume and it is causing downloads to faul since the connection is not ready.

By the way i'm talking about wired Network here. I already entered the ip address manually so it doesnt have to wait for dhcp but it seems to just take a few seconds....

---

