---
title: "Ubuntu 10.04.4 LTS Production server went into hung state"
date: 2014-05-06
forum: General Help
---

### Post by Riunixteam on 2014-05-06
Hi Team, 

One of our Ubuntu Production application server went into hung state at 20:00 BST on 1st May 2014. 

1.       There was no update in any of the system log files after 20:00 BST and monitoring logs
2.       The Resource utilization was very low when the system went into hang state
3.       CPU Utilization was 1.4%
4.       3.13 GB of physical memory was free on the server
5.       Very low or no disk related and network IO is observer on the server
6.       We can say the server was idle before it went into hang state.
7.       After hard boot of the server the system is up and running normally.

Kindly check the attached vmware backup logs during that time and suggest the cause of hung state.

---

### Post by Gyokuro on 2014-05-06
Hi

In your log file you haver snapshot error=35 and indicates a problem with your snapshots: 

kb.vmware.com/selfservice/microsites/search.do?cmd=displayKC&docType=ex&bbid=TSEBB_1297204420024&url=&stateId=1 0 258034597&dialogID=258020911&docTypeID=DT_KB_1_1&externalId=1015180&sliceId=2&rfId=

check the timing of your snapshots maybe something is overlapping.

- HTH

---

