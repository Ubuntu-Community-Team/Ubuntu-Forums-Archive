---
title: "sequel database on NFS (other) bad practice?"
date: 2016-08-25
forum: General Help
---

### Post by Drenriza on 2016-08-25
Hi all

Recently i fell across different articles that said that having a sequel data directory on a NFS with a single client, ISCSI / other is bad practice.

But none of these articles dive into why this would be bad practice, are they afraid of corruption over the LAN links or that the shared drive get something wrong or what is the bad practice in?

Buying a single server with high CPU and memory capabilities and a single server with fast I/O + storage is cheaper that buying a combo server that has both.

What do you think about this? Do you do this yourselves and break the "good practice" rule?

---

### Post by SeijiSensei on 2016-08-25
When you say "sequel," I'm assuming we're talking about SQL servers here?

I'm sure the number one concern about having, say, /var/lib/postgresql/, on an NFS mount is the possibility of data loss should there be a power or network outage.

I see no advantage to this arrangement myself.  I'd rather have the data reside on the same server as the application and connect to the server over IP.

---

### Post by Drenriza on 2016-08-26
> I'd rather have the data reside on the same server as the application
What if this is not possible and you need to split up the application and SQL server?

Lets say that the application itself has so much work, that the resource overhead for also doing SQL on the same machine would break it.
Is the answer than "just" to get a more powerful machine?

> I'm sure the number one concern about having, say, /var/lib/postgresql/,  on an NFS mount is the possibility of data loss should there be a power  or network outage.

Totally valid, but Is this not the same concern as having a SQL server with no write cache (with write protection), and than you from an application somewhere send data to this machine.
After the TCP/IP get an ack back that the data is "delivered" to the NIC but not written to disk, you experience a power outage?

---

### Post by SeijiSensei on 2016-08-26
> **Drenriza said:**
> What if this is not possible and you need to split up the application and SQL server?
Lets say that the application itself has so much work, that the resource overhead for also doing SQL on the same machine would break it.
Is the answer than "just" to get a more powerful machine?
I'm not the guy to ask about that as I have never written such an application.  I write webapps with SQL backends and usually don't have any performance or contention issues.  They're hosted on a virtual server at Linode.  In my experience the SQL server overhead is pretty minimal.  What percent of CPU time is occupied by mysqld or postmaster?  

When I've had SQL performance issues like slow queries, it's almost always because the database is not well-indexed.  There should be indexes for most every set of WHERE criteria in the application.  I once wrote an office-based app that had a database of about 2-3 million records.  It was horribly slow at processing queries until I created the appropriate indexes.

In the case you describe, isn't the limiting factor disc read/write speed more than the efficiency of the SQL server daemon process?  Have you gone though all the manuals online about tuning the server's performance?  I could see splitting the application and SQL server if you want to put the latter on a box with 15K drives in a RAID array.  What kind of load averages do you see with both the app and the server running side-by-side now?

> Totally valid, but Is this not the same concern as having a SQL server with no write cache (with write protection), and than you from an application somewhere send data to this machine.
After the TCP/IP get an ack back that the data is "delivered" to the NIC but not written to disk, you experience a power outage?
:D I use async NFS transfers on my local network so no, I'm not personally worried about such an unlikely event because the server is on a UPS managed with apcupsd.  I find most "official" documentation way too paranoid about things like power outages because they are preventable.  Is there a chance of data loss between my home server and a client machine?  Yes, but it's not very likely.  My virtual servers are all on honking big power supplies in clean server rooms.  I don't worry about them at all.

If this is an important application in production, then sure, split them up and put the most CPU-intensive half (probably the app itself) on the higher-powered machine.  Stick a good, [Linux-supported]("https://wiki.debian.org/LinuxRaidForAdmins") RAID card in the other machine along with 15K drives.  I prefer hot-swappable ones myself.

---

