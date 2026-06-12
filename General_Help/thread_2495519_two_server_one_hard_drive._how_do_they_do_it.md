---
title: "two server one hard drive. how do they do it?"
date: 2024-02-21
forum: General Help
---

### Post by josephchrzempiec on 2024-02-21
Hello, I was just curious on how is it possible to do two servers one hard drive?  So if a server fails the second one can take out without having any down time. I was watching a video on level1tech and he had a server that had two nodes and hard drives. So if One failed the other can take over automatically. He called it a interposer. Not sure sure what that means in turn for a hard drive. I can't seem to find the video to finish watching it sinse it from a few years back. 

I was curious what he meant the interposer and how two nodes can share the same hard drive. Can someone please help me to understand this?

---

### Post by ActionParsnip on 2024-02-21
You can have a drbd file system which replicates between the two servers with one being the active node. You can use pacemaker to form the cluster.. Is this what you mean or do you actually mean one physical disk for two servers?

---

### Post by TheFu on 2024-02-21
> **josephchrzempiec said:**
> Hello, I was just curious on how is it possible to do two servers one hard drive?  So if a server fails the second one can take out without having any down time. I was watching a video on level1tech and he had a server that had two nodes and hard drives. So if One failed the other can take over automatically. He called it a interposer. Not sure sure what that means in turn for a hard drive. I can't seem to find the video to finish watching it sinse it from a few years back. 

I was curious what he meant the interposer and how two nodes can share the same hard drive. Can someone please help me to understand this?

A single server is a single point of failure, so anyone building HA systems wouldn't do that.  Servers (the hardware) may have redundant power supplies, redundant networking, redundant paths to SAN storage, redundant fans, redundant internal buses ... but a single server is still a single point for a fault.  

Typically, a "node" is placed onto different server hardware and there is some sort of redundant storage, redundant networking, redundant processes, and a heartbeat that 2+ nodes used to keep track of the other nodes in the "cluster".

I've never hear the term "interposer", but I only designed HA system for huge businesses for 15 yrs.

There's no single solution to HA.  How it gets done depends on the criticality of the processing.  If you are doing credit card transactions, you'll have redundant data servers writing to redundant databases located in data centers at least 500 miles apart.  This is slow, but writing the transactions to two physically separate DBMS is part of the cost of doing business.
If the system can tolerate losing 5-20 seconds of transactions, then some sort of DBMS replication would be used and the data server only writes to 1 of the servers, then that server would replicate the data to the others within 20 seconds.  The DBMS servers can be active-active, master-slave, master-reporting, master-slave-slave, or primary-failover.  Primary-failover would have the longest time to recovery. Active-Active means that any client can connect to either DB server and the DB updates would be cloned to the opposite server automatically.  Of course, "automatically" isn't really true. The DBA has to set this up correctly and the application needs to be written in a way that prevents deadlocks from different clients trying to modify the same records.

As we move up in the tiers, more and more of the HA becomes using Virtual IPs and something like VRRP in the switch hardware to recognize when an IP has become unresponsive (i.e. the server [software] is dead).  When the server is dead, some method of knowing it is dead and taking over the virtual IP is used.  

So, you have 2 servers, each with 2 NICs connected to 2 different managed switches that support VRRP (or whatever the switch maker calls their equivalent technology).  The NICs in each server are specifically installed into separate PCIe buses, so if 1 bus fails, the other will keep going.  This way the server won't completely lose networking.  Now either DNS is used for load balancing between the 2 server (or it could be 100+ servers for big installations) or the VIP is assigned to 1 server and only gets move to the other server on failure of both network connections.

Redundant storage works similar, either with iSCSI networking or with fibre channel connections into the storage frame. We usually connected 2x the number of fibre connections into the frame as our expected transactions required.  2 or 4 were extremely common.  They were "bonded" connections, so they handled both failures and doubling or quadrupling total throughput from the storage frame.  

Inside the storage frame, there would be hundreds of disks, usually in 4 or 8-way stripes and mirrored.  This means that a single disk seldom was the bottleneck for performance, but disk I/O doesn't scale linearly with the number of disks.  Some math shows that the average, real-world, throughput difference between a 4-way stripe and an 8-way stripe is less than 15% more.  Using a 4-way stripe was mandated where I worked, but 8-way and 16-way were also allowed, if the admin and DBA felt it was needed and they were buying enough storage to own the full drives.  SAN frames are normally too expensive for any single project to fund themselves. It is common for 50-100 different projects to share the same frame, which makes upgrading firmware a complex problem. It is like trying to get the UN to agree on anything unanimously.  Never happens.  So, the installed firmware version was usually stuck for 3-5 yrs and projects that wanted newer firmware would be migrated (and pay) for the new frame.  Eventually, the older projects wouldn't be able to fund the support for the older frame and would be forced to migrate too. Then the frame would be retired and a new frame installed in that DC location.

Firmware updates for frames, SAN switches, server HBAs, and all the ethernet stuff too were a complicated thing.  But when you want HA, all these things needed to fit together.

And we haven't even talked about custom application code to support HA.  Vendors seldom create code with HA at the front of their minds, so we had to teach them how to write their software so that standard HA methods could be deployed.  That often took 1-2 yrs, expect for web servers, which have an architecture that can use fairly standard HA deployment methods.

How can two systems share the same storage?  Use a NAS.  Setup ClusterFS/GlusterFS or some other sort of clustered file systems.  [https://docs.gluster.org/en/latest/](https://docs.gluster.org/en/latest/) I always liked "sheepdog" for my VMs. [https://sheepdog.github.io/sheepdog/](https://sheepdog.github.io/sheepdog/) There are lots of methods.  Google "cluster file systems".  For a home user, setting up a NAS running NFS is about the simplest method.  Virtual machines managed by VPS providers often use NFS for the storage back ends.

[https://tldp.org/HOWTO/openMosix-HOWTO/x135.html](https://tldp.org/HOWTO/openMosix-HOWTO/x135.html) is an intro to clustering - though I've never heard of the specific tool that article mentions.

---

### Post by josephchrzempiec on 2024-02-21
Hello all. Thank you very much for the help and information trying to understand all this. It is something I never heard before until I saw that video a week ago And that video was 2 years ago. If I ever find it i'll post a link in here about it. As for ActionParsnip I honestly don't know what the full story is from the video before I lost it. What I do remember is that it was 2 node servers in a single box that shared or used the same drive from what I remember. It was literly from what I remember 2 nodes in a box with hard drives in the front. 

And from The Fu I did from what I remember heard the word San server. But it was a full server not just a Jbod box. It might have been something you are talking about as what I'm reading of yours.

---

### Post by TheFu on 2024-02-21
EMC, Hitachi and NetApp make SAN storage systems, also called "storage frames".  You and I are unlikely to have them at home.  

At a job in the early 2000s, my project spent $3M on storage that was inside EMC frames in 3 different locations/states.  It wasn't cheap.  I'm embarrassed to say how little storage that bought at the time, but I have about 20x more storage in my house today than we bought.  Enterprise storage solutions do all sorts of things we can't do easily at home, though some of those standard things are much easier at home these days.  Of course, enterprise storage technology has kept moving for better redundancy, faster connections and much greater overall performance.

I attended many weeks of training to learn these things - that training was both high level and hands-on.  Unfortunately, we weren't allowed to use Linux at that company, so it was all Unix based training and used proprietary software.  But the ideas are all the same, even in with our F/LOSS stacks of software.

---

