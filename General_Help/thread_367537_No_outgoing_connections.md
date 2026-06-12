---
title: "No outgoing connections??"
date: 2007-02-22
forum: General Help
---

### Post by icehammer on 2007-02-22
i had intitially set a restrictive firewall policy thru firestarter. but then i changed it to permissive. after that i launched gtk-gnutella, nothing happened.... still nothing happens..!!! 
what to do??

i hv 0.96.1 stable (gtk-gnutella).. i tried logging off and in, still no go...

---

### Post by chggr on 2007-02-22
If you're attempting to run a gnutella client behind a firewall, the default gnutella port is probably blocked (port 6347).

Open firestarter and go to the Policy tab.
Make a new rule so that port 6347 is open for inbound and outbound connections.

---

### Post by icehammer on 2007-02-23
Did that.. still nothing.

Tell me, in Preferences, it says its listening to port 62147... should i open that too?? both incoming and outgoing?

---

### Post by chggr on 2007-02-23
Yes. Practically you should open every port Gnutella uses.

You can also try to shut down the firewall to see if it's working that way. Open a terminal and type:

sudo /etc/init.d/firestarter stop

This command is used to stop the service firestarter, namely your firewall. Check now if Gnutella is running OK. If it isn't, then you don't have a firewall problem and something else is causing Gnutella to misfunction. If it is, it means that the firewall doesn't let Gnutella connect and you should try to configure it better. In the above command, changing "stop" to "start" causes the firewall to start running again.

---

### Post by icehammer on 2007-02-24
I tried that, but nothing happens even now.. will upgrading the version of gtk-gnutella help??

---

