---
title: "Archiving a folder."
date: 2008-03-17
forum: General Help
---

### Post by teishu on 2008-03-17
Hi,
I'm trying to archive a 3GB VMWare image as a snapshot backup and when i right click > 'Archive' it starts going but takes forever.. I check the CPU usage and its like 3.4% and nothing else is running. Why would it not use more CPU usage ?? Surely it would be much quicker ? Any thoughts ?

Thanks

---

### Post by gobbles414 on 2008-03-17
> **teishu said:**
> Hi,
I'm trying to archive a 3GB VMWare image as a snapshot backup and when i right click > 'Archive' it starts going but takes forever.. I check the CPU usage and its like 3.4% and nothing else is running. Why would it not use more CPU usage ?? Surely it would be much quicker ? Any thoughts ?

Thanks

I'm not an expert. But I wouldn't advise trying to archive a VMWare or VirtualBox image. The information inside thees kinds of images is very complex, and could be damaged by the compression that happens during the archival process. I also doubt that the size of your image would get much smaller with archival anyway. Again, I'm not an expert and I could be totally wrong. :KS

---

