---
title: "Is that possible configure 2 Ubuntu Virtual box in my MAC as NFS server and client?"
date: 2016-05-08
forum: General Help
---

### Post by weiqi3 on 2016-05-08
I have a general idea to configure two Ubuntu VM on my laptop as a NFS server and client, I want to know is that possible to do this? If yes, how does this two VM communicate?

---

### Post by TheFu on 2016-05-08
yes.
Treat each VM like a normal system and use normal network protocols to communicate.  The way that I'd do this is to use "bridged" networking for both VMs and put all 3 machines on the same subnet.  Use a static IP for each - you can either set them to be static or setup the router to use "DHCP reservations", if your router supports that.  The 2nd method is best for a laptop that changes networks.  Expect this will not work without manual intervention on other networks, since there won't be any DHCP reservations at the local cafe or coffee shop.

So - after the 3 systems have static IPs (effectively), normal NFS client/server stuff applies.  Since NFS is based on IP addresses, that means the IPs are critical.

Of course, when you are away from home and NFS becomes harder to use, then use something like sshfs to connect the different VMs to storage.

I don't put NFS servers into VMs for a few reasons.  It is about the only "service" I run on VM hosts besides those things required to host VMs.  Everything else goes into VMs.

If the hostOS is Linux, I'd strongly recommend you use KVM instead of virtualbox to get the improved performance and server-class stability.

How do the two VMs communicate?  Over TCP network protocols just like any other system-to-system communication. That can be ssh, http, sftp, scp, https, or any of the 50K other network protocols.  Just be certain to have highly selective firewalls enabled so that open wifi doesn't mean open files to the entire world when you are away from the home/work network.  Depending on your paranoia level, Kerberos-based server-to-server authentication might be the best choice.

---

