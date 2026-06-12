---
title: "How to Keep CUPs file from accumulating logs?"
date: 2016-01-24
forum: General Help
---

### Post by dswaugh on 2016-01-24
Have 14.04 installed on a dedicated 256GB SSD, and all told, the entire installation takes up about 11GB of space. Couldn't boot the OS this morning, though, because the SSD was somehow full. After using disk usage analyzer, noticed that the culprit was the CUPs folder at var/log/cups. It contained a ton of log files that consumed nearly 211GB of space (and promptly filled my SSD). Long story short, I deleted the entire lot of log files from the CUPS folder, and Ubuntu is back up and running (and once again, Disk Usage Analyzer indicates that my drive is only 11GB full). Just wondering how I can keep unwanted log files from multiplying like rabbits in the CUPs folder again. Thoughts anyone? Thanks much.

---

### Post by howefield on 2016-01-25
Something is clearly wrong when the log files get spammed to that extent, so the best way would be to read the logs, find out what it is complaining about and act on the information.

So, what was in the logs ?

---

