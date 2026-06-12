---
title: "Configuring BackupPC for Computers Behind Routers"
date: 2007-08-23
forum: General Help
---

### Post by KawiRider on 2007-08-23
Hello,

I help manage a small network of Windows computers at a research facility.  My supervisor and I have chosen to create a simple backup server using Ubuntu 7.04 and BackupPC.  The problem is, we've only been given a limited number of IP addresses from the University that maintains this facility's internet.  As a solution, we recently purchased a few routers so that we can group machines under one IP address, in turn freeing up IP addresses for later use.  So in short, we have some computers that have been statically assigned IP addresses (with corresponding host names) and some routers that have statically assigned IP addresses (with corresponding host names) and also have computers behind them under the common 192.168.XXX.XXX local network.

I recently built the Feisty backup server and have statically assigned it an IP address given to us by the University.  I can successfully backup Windows PCs that are also statically assigned IP address (i.e. not behind routers).  The problem, however, is that I can't seem to figure out how to backup PCs that are behind the routers.  I'm using samba and have set up file sharing on the "routered" computers exactly how I set up file sharing on the "non-routered" computers.

To further illustrate the situation:

server.university.edu -> internet (campus network?) -> router.university.edu -> computer(NETBIOS).university.edu

How can I backup computer.university.edu?

---

### Post by KawiRider on 2007-08-23
I've looked into it a bit more and I'm not sure but I think I'm going to have to do some forwarding.  I'm going to try using the rsyncd xfer method, forwarding the rsyncd port and hope for the best.  *If* that works, how would I be able to access other machines behind the router, besides the one that has already been forwarded the rsyncd port?  Can I forward that same port to all computers on the internal network?  I don't understand how the server will know which computer to back up in that case...

Regards,
KawiRider

---

### Post by wirelessmonkey on 2007-08-23
Time to set up some VLANS... make sure that your numbering scheme is in order. Each router between server.university.edu and computer.university.edu should have a port on the subnet you choose to use, and each router needs to be tagged on that interface.

---

### Post by KawiRider on 2007-08-24
Thanks for your reply!  The forwarding didn't work as planned.  Could you by any chance point me toward some useful VLAN guides, or perhaps elaborate on what you mean?  I'm just starting to get the hang of networks, and setting all this up in linux makes it significantly more difficult.  Thanks again.

---

### Post by KawiRider on 2007-08-24
I've done some google searching and have not found any intuitive guides to setting up VLANs.  We primarily use DLINK DI-604 routers which have a "Virtual Server" feature but I really have no idea how to set it up for even just one computer behind the router, let alone up to four.

Thanks,
KawiRider

---

