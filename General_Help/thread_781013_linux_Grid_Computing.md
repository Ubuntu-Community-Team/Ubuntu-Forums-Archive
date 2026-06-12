---
title: "linux Grid Computing??"
date: 2008-05-03
forum: General Help
---

### Post by helbuns on 2008-05-03
Hi ubuntu, i come here because this is where i get all my linux help... and i need some direction. i currently am a student a Chubb tech in NJ and we have like 100 machines my teacher and i would like to add to WorldCommunityGrid as part of a private grid cluster?? i guess is what you could call it... a few issues... being a school they have assigned hard drives that get locked away when not in use... so these machine are pretty much 2.8 ghz 1gb ram no hard drives networked. we want to get them all to work together because we hope to get a performance boost... we have a number of old servers to manage them but myself and my teachers are really not sure about the best way to go about setting up the grid. im really not sure what OS's i need or software. i know CentOS does clustering but im not sure if thats what i want or if that is what is best. i guess i would be looking for someone to help direct me and my teachers and class mates.

again we want to run boinc over a distributed grid to practice load balancing and see performance, a small live cd os with networking i guess would work that waits for instructions from a master, but again i really just dont know where to begin looking... and i dont expect this to be easy, but fun. plus we are gonna rock WCG!!
so i guess this is a beowolf cluster but i dont really know anything... ive been using linux for like 7 months and it rocks... i have over 30 different linux OS virtualized now and familiar with c++ ruby perl python http php mysql alittle fortran and others all thanks to linux and it all started with ubuntu 6.04. man.... best thing that ever happened to me... also... i just learned to install slackware.. that was pretty big.... and im learning the BSDs.... they are just cool. im also learning vi editor (so hard) and lynx (firefox is just so slow(i kinda hate what flash has done to the web)) that you ubuntu for helping me in the past, i just hope i can give back computing cycles and one day program for ubuntu mobile and embedded!

thank you for your time
Sean

- Linux now and forever

---

### Post by gsmanners on 2008-05-03
I don't know too much about it myself, but I assume you're trying to do something like this:

[http://www.boinc-wiki.info/Creating_a_diskless_cluster](http://www.boinc-wiki.info/Creating_a_diskless_cluster)

---

### Post by wirelessmonkey on 2008-05-03
There are a number of ways to do what you want. In my opinion, the easiest is to download a live cd that is cluster capable, probably with MOSIX or OPENMOSIX.  Set up a primary node on a server, set up a second server as a PXE and DHCP server for your cluster.
Assuming your network infrastructure is up to snuff, you should be able to PXE boot the Live CD iso, if you have enough system memory you will be able to grid through your primary node.

I suggest using the Knoppix Cluster Live CD [http://www.knoppix.net/wiki/Cluster_Live_CD]("http://www.knoppix.net/wiki/Cluster_Live_CD")
simply because I have some experience with it.

I've not used an HD free cluster before, so there may be some extra tinkering to be done, hopefully this will get you started.


Best of Luck

---

### Post by helbuns on 2008-05-06
Hey guys thank you so much for your speedy replies, these links are exactly what i need and will provide awesome resources for future endeavors, ill make sure to document my progress to make the process easier for others.

sean

---

