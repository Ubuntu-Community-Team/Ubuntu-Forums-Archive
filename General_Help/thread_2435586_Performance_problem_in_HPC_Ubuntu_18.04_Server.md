---
title: "Performance problem in HPC Ubuntu 18.04 Server"
date: 2020-01-22
forum: General Help
---

### Post by noahf19 on 2020-01-22
Hi!

I've got an HPC related issue with my 40-core/80-thread Ubuntu 18.04 server, w 256 GB of RAM. I'm running a multi-threaded JVM process - AWS Java 11 - and four times an hour (in a regular pattern) the CPU slows down from roughly 3,600% CPU to 300%. I've checked the JVM logs and it appears to be garbage collecting normally. Network and RAM are all nominal. I am seeing a spike in the Raid 0 software component which hits 100% utilization (confirmed via atop and iotop) and exactly coincides with the performance drop-offs. This behavior seems to be independent of changes to the process stack, because I dramatically reduced the file IO and am observing the same behavior.   

Has anyone ever seen this issue?

If so, is there a patch out there?

---

