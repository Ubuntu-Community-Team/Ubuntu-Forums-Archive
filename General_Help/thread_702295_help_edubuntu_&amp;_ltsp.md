---
title: "help: edubuntu &amp; ltsp"
date: 2008-02-20
forum: General Help
---

### Post by whiskey29 on 2008-02-20
Hi all, first of all, I'm a linux convert :) Been using ubuntu for a months now, read lots of article, how to's and tweaked my desktop and laptop alot. 
I stopped using m$winblows except for games now.
If commercial games start running in linux, I'll never use m$ again :)

I'm building an office and I'm looking into using ubuntu with ltsp for the 10 clients.

to avoid ltsp setup headace, i have already installed edubuntu server right away.

Now with ltsp, does it do domain like login which stores username and configuration ?
Can I setup a parallel edubuntu server in case one server is down I'll have backup automatically.
can somebody point me to good literature besides ltsp.org or the ubuntu wiki.
I'm stil figuring out the network topology for the parallel server. Currently I will have 5 client on 1st floor and 5 on 3rd.

so i should have 2 nic for the server. 1 which connect to the router and from here goes to internet gateway, the gateway it self has another conenction to dsl modem. (which i have zonecd for the hotspot configuration).
the other nic would connect to a switch on 1st floor which connect to 5 clients.
the other 5 clients on the 3rd floor will conenct to a switch, and that switch will connect to the switch on the 1st floor.



To be honest, most guide and man are too difficult for beginer like me to read and understand. If everything could be friendlier I bet we will have more ubuntu user :)

---

### Post by maybeway36 on 2008-02-20
> **whiskey29 said:**
> Now with ltsp, does it do domain like login which stores username and configuration ?
Not quite - you log on directly to the server, the clients are only for display and input. So essentially, it's like you're at the server.
> **whiskey29 said:**
> so i should have 2 nic for the server. 1 which connect to the router and from here goes to internet gateway, the gateway it self has another conenction to dsl modem. (which i have zonecd for the hotspot configuration).
the other nic would connect to a switch on 1st floor which connect to 5 clients.
the other 5 clients on the 3rd floor will conenct to a switch, and that switch will connect to the switch on the 1st floor.
Yes, you should have 2 NICs, one to the Internet and the others to the clients. The clients don't need to be connected to the Internet, just the server. You should probably connect the server and first switch, as well as the first and second witches, with gigabit if you can.

---

### Post by whiskey29 on 2008-02-21
Thanks for the reply :)

So basically I just need to create accounts for them, since in linux each user can be totally restricted then it's better than domain !!!

I just bought 2 switch today but they have no gigabit. only 100, Thanks for the tips, I can see now that connection between routers gonna need a lot of bandwith.

---

