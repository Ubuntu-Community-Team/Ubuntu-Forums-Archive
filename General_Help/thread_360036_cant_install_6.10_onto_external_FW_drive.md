---
title: "cant install 6.10 onto external FW drive"
date: 2007-02-12
forum: General Help
---

### Post by goucho29 on 2007-02-12
750Gb external FW drive, attached to my MBP. Just moved all data of the FW drive so I can start clean. I began by preparing 5 partitions on the FW drive:

a. 44 Gb non journaled HFS+
b. same
c. 87 Gb journaled HFS+
d. 174 Gb journaled HFS+
e. 350 Gb journaled HFS+

Im hoping to install 6.10 to the a. partition. I boot the CD, get to the install icon on the default screen, and go step by step thru its installer...

Get to Prepare partitions section where it asks where I would like 6.10 installed and Im asked to pick a partition. I can see that I want the first 44Gb chunk (in this case mapped to sdb3)
Groovy, select it then choose Forward button

Next screen: Prepare mount points. 
1. choose first mount point / mapped to sdb3. 
2. choose 2nd mount point swap to sdb3 as well

Click Forward button ? Nope, not possible
Check Reformat checkbox for either mount point ? 
Nope not possible. 

so - what is going on ? 

Meanwhile my Mac using friend is getting alot of work done whilst I putz around...

---

