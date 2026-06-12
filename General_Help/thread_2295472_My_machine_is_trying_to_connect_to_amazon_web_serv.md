---
title: "My machine is trying to connect to amazon web service right after login..."
date: 2015-09-18
forum: General Help
---

### Post by rhiltbrunn2 on 2015-09-18
Ubuntu MATE 14.04 64 bit
HP Pavilion dv-6xxx

I just got an application crash notice after logging in from a boot up. (suspend/resume failure)
While looking in the syslog I noticed a connection to  50.18.192.251 which is: Amazon.com, NetName: AMAZON-EC2-8, Amazon Web Services, Elastic Compute Cloud, EC2
(I've got my syslog saved if it is needed)

So, I'm wondering why my machine would be trying to connect to an amazon web service after login? I don't remember setting anything up that does that.

I'm realatively inexperienced with linux, so I'm not sure where to start looking. 

Any ideas as to what might be going on and how I might proceed, in order to investigate further, would be very appreciated.

Thanks
Rich

---

### Post by TheFu on 2015-09-19
That IP is a duckduckgo.com system.  Is that a saved/default webpage in your browser?
Lots of different companies use Amazon EC2 for their servers.

---

