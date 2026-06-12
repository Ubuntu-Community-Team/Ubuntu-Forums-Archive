---
title: "NTP Drift File drifting"
date: 2012-11-20
forum: General Help
---

### Post by Meadowlander on 2012-11-20
Guys,
 
I have a problem maintaining a stable NTP sync in the following Network configuration:
 
PC1 connected to PC2 connected to PC3
 
All of them are running different Linux distributions. PC 2 and 3 run a NTP server. PC3 is hooked up to a GPS receiver and hence has the most accurate time. Only PC3 is powered on continuesly, PC2 is opperating for 2 to 6h a day, while PC1 is opperating almost the same time as PC2. 
 
Here is how they are supposed to sync:
PC3 syncs to GPS - works great
PC2 syncs to PC3 via NTP - works great
PC1 syncs to PC2 via NTP - here is the issue
 
PC1 syncs real nice to PC2 for about a week or so. After a week NTP traffic on the network skyrockets with about 2 NTP polls every second to PC2, time sync gets really bad - in the order of seconds, at least according to the NTP message content. 
If I do an ntpq from PC3 to PC1 I see the following:
- Time sync is in the order of 10 ms
- Every 10 seconds the daemon on PC1 stops responding
 
If I do an ntpq from PC1 to PC3 I see massive jitter between +2ms and -10ms.
 
Here is the fun part: If I reset my ntp.drift files frquency drift on PC1 to -2.00 everything works fine again. After a week the drift file changes to a value arround 1 (last week) and arround 35 this week leading to the problems described above.
 
As a heads up: The network architecture shall be maintained.
 
Anybody any ideas what the problem is?

---

### Post by Meadowlander on 2012-11-21
Somebody having any ideas?

---

