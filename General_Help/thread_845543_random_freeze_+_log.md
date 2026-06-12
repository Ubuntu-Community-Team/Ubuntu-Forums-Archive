---
title: "random freeze + log"
date: 2008-06-30
forum: General Help
---

### Post by ost2life on 2008-06-30
Okay, this is the closest I can get to a log of the actual crashes that keep happening.

I've edited the log down to just the moments before the crash:
kern log
Jun 30 22:21:52 upstairs-desktop kernel: [  804.866312] synaptic[5537]: segfault at 771954a5 eip b78d20de esp bf894ff0 error 4
Jun 30 22:22:15 upstairs-desktop kernel: [  827.968133] Eeek! page_mapcount(page) went negative! (-1)

messages
Jun 30 22:21:52 upstairs-desktop kernel: [  804.866312] synaptic[5537]: segfault at 771954a5 eip b78d20de esp bf894ff0 error 4

syslog
Jun 30 22:21:52 upstairs-desktop kernel: [  804.866312] synaptic[5537]: segfault at 771954a5 eip b78d20de esp bf894ff0 error 4
Jun 30 22:22:15 upstairs-desktop kernel: [  827.968133] Eeek! page_mapcount(page) went negative! (-1)

I just need someone to tell me that either I've killed something hardware based or the kernel is just rubbish.
Please! this is doing my head in.

thankyou in advance.

Paul

---

