---
title: "Redndancy on Linux Server"
date: 2013-12-19
forum: General Help
---

### Post by marius4 on 2013-12-19
Hi. I currently Have a Ubuntu Server (12.04 LTS) running on HP Hardware with 5 NIC's . Two of the 5 NIC's are bonded and service 12 VLANS (Connected to Cisco Switches). The other 3 NICs are each connected to a Cisco DSL Router.
This Server Is Currently Used as the DNS Server; DHCP Server; Mail Server; Router between VLANS; Firewall; VPN Server;RADIUS Server,ftp
I have another HP Server with the same Hardware Specs that I want to Use as a Redundant Server in case the one above fails ( High Availability) 

What is the best scenario to use for redundancy on the running services? 

I have looked at DRBD  and also thought of running Ubuntu Server on XEN..(I believe XEN does not support that many NIC's).

---

### Post by tgalati4 on 2013-12-19
What is your definition of High Availability?

You already have degradation capability using multiple NIC's--if a card or switch or link fails, you will still have throughput, although degraded.

I would make a mirror image of the server configuration and make sure it boots on the new (backup server)--you may have to fix block ID's on the disks if you just do a simple mirror.

Then I would wrap the server in several layers of plastic and write the date using a Sharpie and store it away from original server.  If your operational server fails, unwrap the plastic and install the new one and boot.  You should check the backup once a year, perform any updates, run it for 24 hours to check for stability, and rewrap and date it.

Having a second server running as a standby will cost more in electricity and wear-and-tear than simply buying something newer and more energy efficient--and possible configuration change.

Having a wrapped spare will save you from smoke, water, fire, power spike, lightning strike, construction dust, etc, things that are more likely to happen than simple hardware failure of network components.  With a clean environment, controlled temperature, and buffered power, you can get 5, 7, 10 years of continuous uptime.

There are several web tutorials/blogs on best practices for HA, but it really depends on how many millions of dollars of business per hour are transacted.  For a small business, having a hardware spare that you can boot within an hour should be sufficient.

Of course, you need to have some monitors set up on your server so you get instant notification when bandwidth, temperatures, fan speeds, etc go out of bounds.

Every two years, I would take the server down (swap it with the wrapped spare) and completely go through it--clean and reseat everything and then run it for 24 hours to test for stability.  Then if it passes, put it back into service.

Xen may be a good solution if you need a lot of virtualization, but I'm not sure how it helps with HA.  You would need to share your Use Case in more detail.

A Haiku:

Downtime cost--How much?
High Availability?
Spare at the ready.

---

