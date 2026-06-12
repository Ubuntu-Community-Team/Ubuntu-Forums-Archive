---
title: "Xubuntu 7.04 memory leak? with PHP5, Apache2 and MySQL"
date: 2007-06-20
forum: General Help
---

### Post by blankko on 2007-06-20
I'm currently using Xubuntu 7.04 with MySQL PHP5 and Apache2 installed.

I think I'm experiencing memory leaking from one of the above mentioned software package.

Before are graphs I've recorded between system crashes from the memory leak.

System Load:
[IMG]http://farm2.static.flickr.com/1420/573670862_9b4a16cfd9_o.png[/IMG]

Processes:
[IMG]http://farm2.static.flickr.com/1077/573670882_96c76cb2a3_o.png[/IMG]

Memory Usasge: (I have 256mb of ram, the graph displayed the value incorrectly as 'K' should be 'M')
[IMG]http://farm2.static.flickr.com/1098/573670874_dbccca4f41_o.png[/IMG]

The empty part of the graph is due to rebooting from previous crash and crashing again.

The system didn't exactly crashed. With all the physical and swap memory used up, the system became so unresponsive that it was unusable.

Anyway for me to track the cause of the problem.

---

