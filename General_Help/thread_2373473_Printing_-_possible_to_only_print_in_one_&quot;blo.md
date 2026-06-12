---
title: "Printing - possible to only print in one &quot;blob&quot;"
date: 2017-10-06
forum: General Help
---

### Post by csdgbas on 2017-10-06
Is it possible to configure things such that print-job data is sent to the printer as one single "blob"? The network is so unreliable that I can get part way through a print job and data gets lost ("Unable to write print data: Broken pipe"), which is not only annoying but can cost money as well.

---

### Post by dino99 on 2017-10-06
printing jobs are sent to a queue first; so if the printing network is not ready, then the jobs will wait.

---

