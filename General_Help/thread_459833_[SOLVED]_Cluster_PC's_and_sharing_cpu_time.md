---
title: "[SOLVED] Cluster PC's and sharing cpu time"
date: 2007-05-31
forum: General Help
---

### Post by nga911 on 2007-05-31
How hard would it be to cluster two desktops or more ? ; if at all possible? Are there any how'tos for this.? 

a windows and linux desktops:p for use with some analysis software. [this]("http://www.flomerics.com/flovent/")

---

### Post by nga911 on 2007-05-31
any help:KS

---

### Post by nga911 on 2007-05-31
help me:(

---

### Post by tutomlin on 2007-07-02
I don't know if you are still looking at this thread, but as far as I know there is no easy tutorial  to set up a cluster in Ubuntu.

If you feel comfortable compiling your own kernel you could check out kerrighed, which is a project that will transfer programs running on a high load computer to a lower load computer in the same cluster.  The downsides are 1 that the interfaces are all unix shell style interfaces so if you'd prefer a GUI you're out of luck. and 2 it's not smp safe yet (they plan to finish later this month) so if you have a dual core computer you may want to skip this.

I feel kinda bad promoting an alternate distro in this forum but the simples clustering I know of is the clusterKnoppix distro.  This allows you to boot new PC's into the cluster simply using a live CD type boot.  It's based on OpenMosix and uses the 2.4 linux kernel and it's supposed to be dead simple to set up.

Hope that helps you out.

Tucker

---

### Post by kevinlyfellow on 2007-07-02
I'm building a Cluster right now for my school.  I'm using debian to do this, and I'd think that it would be a smart choice for a clustering project.  If I were you, I'd go openmosix (a special kernel patch that will distribute the processing information), since you won't need to program anything special for the cluster [http://openmosix.sourceforge.net/](http://openmosix.sourceforge.net/) .  You should really try a livecd first.  Here is a list from the Openmosix site [http://openmosix.sourceforge.net/instant_openmosix_clusters.html](http://openmosix.sourceforge.net/instant_openmosix_clusters.html)

---

### Post by AmericanAqualung on 2007-07-05
Just this past year, I built a cluster for my college's physics department.  Although our hardware is in the terms of server blades and not desktops, our work can be replicated on a small lan of desktops (I've done so in my dorm room for fun).  Depending upon your application, it really isn't hard if given a good guide (unfortunately none really exist).   The most general outline is to install all compilers/etc first.  Set up passwordless ssh between all root accounts, then set up dsh (distributed shell), ntp (network time protocol), nfs (network file system), and some sort of scheduler/resource manager (we chose torque/MAUI).  We've also installed python and mpi on all nodes.  The cluster can handle submission of several serial jobs and parallel jobs.  If you'd like to go this route, please visit my website at <http://students.haverford.edu/aohara>.  While installing the cluster we wrote up our notes as guides for others to follow.  They should be posted within a week or so at my website.  If you'd like to discuss this more either on the thread or off (e-mail me at [email]aohara@haverford.edu[/email]) feel free to.  I'm very excited to extend my own knowledge for linux clustering and ubuntu and helping others do the same.

---

