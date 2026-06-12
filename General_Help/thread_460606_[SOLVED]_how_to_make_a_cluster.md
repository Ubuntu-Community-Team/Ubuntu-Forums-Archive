---
title: "[SOLVED] how to make a cluster ?"
date: 2007-05-31
forum: General Help
---

### Post by nga911 on 2007-05-31
How hard would it be to cluster two desktops or more ? ; if at all possible? Are there any how'tos for this.?

clustering a windows with a Linux for [CFD software ]("http://www.flomerics.com/flovent/")

is it possible :D

---

### Post by tronica on 2007-05-31
I dont' know much about setting up a cluster however i found a few links to look at


[http://ubuntuforums.org/showthread.php?t=16508](http://ubuntuforums.org/showthread.php?t=16508)

[https://help.ubuntu.com/community/UbuntuOnCluster](https://help.ubuntu.com/community/UbuntuOnCluster)

---

### Post by buttari on 2007-05-31
> **nga911 said:**
> How hard would it be to cluster two desktops or more ? ; if at all possible? Are there any how'tos for this.?

clustering a windows with a Linux for [CFD software ]("http://www.flomerics.com/flovent/")

is it possible :D


Hi,
technically a cluster is a bunch of machines networked together and with any flavor of MPI installed on them. From this basic definition a cluster can be way more complex than that. In order to be efficiently usable I would say at least these things are needed (in order of importance):
1) MPI
2) NFS
3) NIS
4) a frontend node
5) a scheduler like OpenPBS if the number of nodes is higher than 16 (maybe even less)
You can easily find howtos for each of these things.
Obviously you don't want to install X on the nodes but maybe only on the frontend node. 
I did it many times but took me a while before getting it right. Overall it is not that difficult.

Alfredo

---

### Post by nga911 on 2007-05-31
thx :p:KS:p

---

### Post by nga911 on 2007-06-01
is there any how to ?

---

### Post by tutomlin on 2007-06-11
hi there,

I haven't had tome to try anything personally but I have done some looking myself

If your looking for some detailed background in setting up a computing cluster for your own code (or somebody else's code you modify) then check out [http://www.clustermonkey.net/](http://www.clustermonkey.net/)

If your looking for something that will automatically "migrate" working apps from high load computers to low load computers, check out Kerrighed and OpenMosix. 
[http://www.kerrighed.org/wiki/index.php/Main_Page](http://www.kerrighed.org/wiki/index.php/Main_Page)
[http://openmosix.sourceforge.net/](http://openmosix.sourceforge.net/)
 As far as I know Kerrighed is more likely to work since it's on the 2.6 kernels now which ubuntu needs to run the x-server properly.  Also, apparently, neither of these plays well with SMP systems so you might have to watch out if you have a dual core computer.


What most people really want (a way to make a single ap like openoffice run superfast) doesn't really exist because programs just aren't written to spread themselves over a networked cluster.  The best you can really hope for is that you'll see some speedup if you keep lots of programs running at the same time since they'll shift around to machines with lower load.

Hope that's somewhat helpful

Tucker

---

### Post by AmericanAqualung on 2007-07-05
Hi, I already posted this on another of your threads asking for help - not sure which you'd check.  It seems that buttari and tutomlin have already given you some good advice but pasted below is mine from the other thread:

"Just this past year, I built a cluster for my college's physics department. Although our hardware is in the terms of server blades and not desktops, our work can be replicated on a small lan of desktops (I've done so in my dorm room for fun). Depending upon your application, it really isn't hard if given a good guide (unfortunately none really exist). The most general outline is to install all compilers/etc first. Set up passwordless ssh between all root accounts, then set up dsh (distributed shell), ntp (network time protocol), nfs (network file system), and some sort of scheduler/resource manager (we chose torque/MAUI). We've also installed python and mpi on all nodes. The cluster can handle submission of several serial jobs and parallel jobs. If you'd like to go this route, please visit my website at <http://students.haverford.edu/aohara>. While installing the cluster we wrote up our notes as guides for others to follow. They should be posted within a week or so at my website. If you'd like to discuss this more either on the thread or off (e-mail me at [email]aohara@haverford.edu[/email]) feel free to. I'm very excited to extend my own knowledge for linux clustering and ubuntu and helping others do the same."

--Good luck.

---

