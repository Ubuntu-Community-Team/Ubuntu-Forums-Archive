---
title: "New install and having ssh -D tunnel problem :("
date: 2007-02-22
forum: General Help
---

### Post by fierce on 2007-02-22
Hi all.. Just did a new install and am having a weird problem :(

I, like most people, just have a plain cablemodem at home with no type of protection from your ISP snooping.. So what I do is create an SSH tunnel to an outside host and route all of my traffic through that port.  (example:  ssh -D13331 -lusername my.shellcompany.com, then I can just enter localhost:13331 as my SOCKS proxy in any internet application and at least its encrypted.)

However, I have tried doing this with VARIOUS sources, and ones that I definitely know have no speed boundaries in place.. I cannot seem to EVER get more than like 90kb/s or 100kb/s when I am downloading through the tunnel.  Downloading directly from any of the sites through something like FTP, not through the tunnel, is getting considerably more, like in the 500-600kb/s range..  Can anyone explain to me why the traffic through the tunnel is so much slower?  Is this some kind of limitation in the SOCKS proxy?  Is my computer too crappy to decrypt the data faster?  I have no idea, if anyone can help or leave some suggestions I will be checking this all night!!!!

Thanks alot everyone! :---)

---

### Post by zanglang on 2007-02-22
Traffic through an ssh tunnel still goes through your cable connection, so it's pretty much limited by your cable bandwidth. ;)

Also because your data has to travel a few more hops to get to you (imagine traffic getting rerouted through more nodes on the internet cloud picture thing), it's definitely going to be slowed down a tad.

---

