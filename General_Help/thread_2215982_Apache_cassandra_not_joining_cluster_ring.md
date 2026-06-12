---
title: "Apache cassandra not joining cluster ring"
date: 2014-04-09
forum: General Help
---

### Post by joy4 on 2014-04-09
Hello,

I've a four node apache cassandra community 1.2 cluster in single datacenter with a seed.
All configurations are similar in cassandra.yaml file.
The following issues are faced, please help.
 
1] Though fourth node isn't listed in nodetool ring or status  command,  system.log displayed only this node isn't communicating via  gossip  protoccol with other nodes.
However both jmx & telnet port is enabled with proper listen/seed address configured.

2] Though Opscenter is able to recognize all four nodes, the agents are not getting installed from opscenter.
However same JVM version is installed as well as JAVA_HOME is also set in all four nodes.

Further observed that problematic node has Ubuntu 64-Bit & other nodes are Ubuntu 32-Bit, can it be the reason?
 
Thanks,
Joy

---

### Post by PartisanEntity on 2014-04-09
Duplicate thread closed. Please only open 1 thread per issue to avoid confusion. Thanks

---

