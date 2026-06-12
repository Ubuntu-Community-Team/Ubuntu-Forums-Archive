---
title: "unblock port for matlab license server"
date: 2007-02-15
forum: General Help
---

### Post by rblack on 2007-02-15
Folks:

I have been trying for some time to get my matlab license server to run on my Ubuntu (Dappar Drake) machine since I installed Ubuntu about 3 mo. ago.   I always get the same error: 

"(lmgrd) Failed to open the TCP port number in the license."

In other words, it appears that the port specified in the license file is blocked so that the daemon can not open it.

I have tried any number of iptable changes,using either firestarter, or using the iptable command directly.  The iptable -L command always shows that the desired iptable change has taken place (e.g. specific port has been set for "ACCEPT"), but the error above still occurs.  

It's almost like a second firewall, beyond iptables,  is in place?  Of course I'm no expert on iptables so I could be making a stupid mistake.  

Of course I never had this problem with RedHat...Any suggestions would be most welcome.


regards rb

---

### Post by ehowell on 2007-02-15
That is strange.

I am running Matlab 2007a on Edgy and can start of it just fine. Of course I can't use the GUI, but I don't believe that is license related.

Is it a single user license? I thought that those were checked against the license.dat file internally, and you are trying to call out through a TCP port.

Sorry, not much help here but maybe we can compare to see what is different about our license managers?

---

### Post by rblack on 2007-02-15
Yes, this is a single user license.  The license manager/server is running on the same machine that matlab is running on.  Matlab makes a TCP "network" connection (all inside the same machine) to the license server on that machine.  

At first glance this seems strange, but that's the way it works.  Idea is to emulate the operation that goes on when connecting to a network license server.

I've had extensive discussions  with Mathworks support folks; the only problem that they can identify with my installation is that something appears to be blocking the port that the license server is supposed to use.

rb

---

### Post by penvzila on 2007-02-20
You already paid for the license, so why not crack the ******?

---

