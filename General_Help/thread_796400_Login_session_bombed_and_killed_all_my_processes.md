---
title: "Login session bombed and killed all my processes"
date: 2008-05-16
forum: General Help
---

### Post by danfluidmind on 2008-05-16
Hi all. I installed 8.04 a few days after it was released and it's been running happily since then. I installed VMware Server Console in order to connect to our main server. It's been working fine. But yesterday, right after I clicked on the Shutdown button in one of the Ubuntu VM servers, my entire desktop went blank, then after a few seconds I got the login screen. I logged back in to my desktop and all of the processes I had running (several terminals, Firefox, VirtualBox, and VMware Server Console) had all been killed.

That's a bit disconcerting. I'd like to know what happened. Has anyone ever encountered such a thing? The only thing I can see in my logs is the following in /var/log/messages:

May 15 17:16:48 ddelaney-linux kernel: [483351.434016] console-kit-dae[5657] general protection rip:7f8345d5d423 rsp:418e2ff0 error:0

Thanks
--Dan

---

