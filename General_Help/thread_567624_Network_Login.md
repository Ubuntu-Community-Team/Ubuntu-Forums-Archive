---
title: "Network Login"
date: 2007-10-04
forum: General Help
---

### Post by ev5unleash1 on 2007-10-04
Well, I currently go to school and they are running windows. There is a login for each student and it has all of there settings and permissions on there account. I want to this with Ubuntu for my Home network. I want it so every computer with Ubuntu on it will login and use one PCs information for permissions and have the same thing for every computer.

Is there a way I can do that? I want all of the PCs in the house be more attached and all of them easier to use.

---

### Post by thhp on 2007-10-05
You could look into using NFS (Network File System) on the "server" PC to export a /home partition to each of the machines on the network.

Since all your desktop settings are stored in your home directory that might give you what you want -- here's a decent starting point for Ubuntu (tho google will be able to help lots more):

[http://anotherubuntublog.wordpress.com/2006/09/14/sharing-folders-between-systems-with-nfs/](http://anotherubuntublog.wordpress.com/2006/09/14/sharing-folders-between-systems-with-nfs/)

For sharing account information, you may want to look into NIS (Network Information Service). Again, here's an introductory link:

[http://en.wikipedia.org/wiki/Network_Information_Service](http://en.wikipedia.org/wiki/Network_Information_Service)

We use a similar setup to this at work, and it allows me to log into my Linux desktop from any Linux box on the network.


Hope this helps.

---

