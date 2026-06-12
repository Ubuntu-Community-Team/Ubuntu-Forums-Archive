---
title: "ubuntu server 12.04, postgresql and hard disk size?"
date: 2013-11-26
forum: General Help
---

### Post by ericmachine on 2013-11-26
Hi everyone,

I plan to setup a virtual machine (in vmware) with the specs below.

2 core
6GB ram
50GB hard disk storage

Just say I choose LVM part of the ubuntu 12.04 server installation (or entire disks).

Inside here, I will have my business applications running in there. 

I assume my postgresql is installed into one of the directories of ubuntu server.

Now my problem. My VM hard disk is fully occupied, say around 95% full already.

I need to add more storage into my VM, which I believe I can. I need to mount a new partition say another 30GB which in total this VM will have 80GB (either as a combined partition, which I am not sure how or 2 partitions).

However if I mount a new partition, but my postgresql is installed on the 1st partition, I don't think it will help either?

A good analog is like windows

say I install postgresql on C:/ drive. When I setup a new D:/ drive, it doesn't solve the issue as postgresql is on C:/ drive.

What should I do? 

I am not looking at NAS or SAN storage for time being. But I wonder how can I scale this VM accordingly? Is there any special ways to make this work?

Thanks in advance.

---

