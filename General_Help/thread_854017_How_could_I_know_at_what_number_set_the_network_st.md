---
title: "How could I know at what number set the network startup script ?"
date: 2008-07-09
forum: General Help
---

### Post by georgesgiralt on 2008-07-09
Hi !
My question seems a bit cryptic...
Here it is in plain English :
In /etc/init.d there is a script starting/stopping network functions named networking.
If I want this script to start at a defined runlevel (sy 2) and stop at another one (guess 6) I've to make soft links in /etc/rc2.d and /etc/rc6.d
The first one will be named SNNnetworking and the later KNNnetworking. 
The NN saying after what particular initialisation the network will start/stop.
I can't find a pice of documentation describing the recomended NN values for the different parts (i.E. NFS should definitelly start after the network but does the network should start before sound server ?)
Any help would be appreciated.
TIA.

---

### Post by kevdog on 2008-07-09
Rather than doing it by hand you should use the update-rc.d executable to add your script to the various run levels:


[http://www.debian-administration.org/articles/28](http://www.debian-administration.org/articles/28)
[http://www.debuntu.org/how-to-manage-services-with-update-rc.d](http://www.debuntu.org/how-to-manage-services-with-update-rc.d)

---

