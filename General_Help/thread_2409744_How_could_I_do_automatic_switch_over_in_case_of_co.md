---
title: "How could I do automatic switch over in case of computer fail (ubuntu 16.04)"
date: 2019-01-06
forum: General Help
---

### Post by adrian-h on 2019-01-06
Please move if in wrong section and sorry for the long intro.

From following written install commands I have a small GPS vehicle tracking server for family and friends, it runs from home and sits behind my home internet router with restricted port forwarding. All seems to be well with the very limited traffic it has.
I am using it to learn more on Linux as I go along, so I will probably make errors as I learn.
I have started to configure a back-up computer, it is a difference type of machine so  just mirroring the HD was not an option.
I have cron jobs that stop the required service on both machines, save the working MySQL database, gzip it, transfer to the backup machine, restore to the backup machine and then start the services again.  So if the live machine fails I could manually change the home internet router to select the back-up machine and work from that.

Now to my question, 

I was wondering if it was possible and how I could achieve it to permanently have the home router forwarding ports to the backup machine, which because it knew the live machine was there, forwarded the TCP packets information to the live machine.  The live machine would still access the internet it self directly.   
I was thinking of some form of regular polling between the live and backup machines which when stopped would signal to stop forwarding TCP and allow the backup to then deal with the TCP information it self?

Is such a thing plausible, and how.

The computers are a couple of HP Thin clients so they are not power machines but cope as mentioned with limited traffic.

Cheers

Adrian

---

### Post by TheFu on 2019-01-07
If you are seeking a "make HA" checkbox, I have bad news.  It is very manual and the admin has to setup everything, every detail, for every service.

To accomplish what you want is called "clustering".  There are many different techniques based on the architecture for the network, each layer of the software stack and storage design.  

So, the first part is to ensure there isn't a single point of failure for the internet connection. That means having 2 different ISPs with separate lines into the location.
Next, ensure you have redundant power and sufficient backup power available. 2 separate systems and a UPS that lasts 2x longer than any power outage you need to handle is a start.
Next, you'll want a load balancer for the service front-ends.  This would use VRRP (or whatever your switch/router supports) on the networking equipment and VIP - Virtual-IP for both servers.  Each serve would monitor the VIP on the opposite server. If the other server stops responding, then the remaining system would take over that VIP. Or you could use a simple reverse proxy like HA-proxy or nginx.  I use nginx for web-services, but for more complex protocols, teaching the client machines how to switch from the primary to the standby IP is necessary.  That could happen inside the client program or it could require the user to specifically change something first.
Next you need to have an Active-Active or Active-Standby DB setup.  The ways to do this are DBMS specific. There are easier solutions if the storage is shared, but you can make something work with near-real-time replication either using log replication or block storage replication.

Many of these things become easier if you run virtualization like KVM with replicated back-end storage through something like sheepdog or gluster or ... one of the other 5 choices.

As you work through all of this, be certain to test.  Pull the power from 1 of the systems.  Grab the network cables and unplug them both - the primary and the redundant cables for each server. 

And don't forget that you need procedures to bring the redundant systems backup post-failure.

If you aren't in love with MySQL, perhaps this is a time to move to postgresql or mariadb?  
[https://mariadb.com/resources/blog/mariadb-maxscale-high-availability-active-standby-cluster/](https://mariadb.com/resources/blog/mariadb-maxscale-high-availability-active-standby-cluster/)
[https://www.postgresql.org/docs/9.0/hot-standby.html](https://www.postgresql.org/docs/9.0/hot-standby.html)

That should get you started. Good luck. You'll learn a bunch.

---

