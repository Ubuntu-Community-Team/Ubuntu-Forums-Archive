---
title: "synaptic not downloading package information"
date: 2006-12-30
forum: General Help
---

### Post by tr333 on 2006-12-30
I had a problem with synaptic where it wouldn't download/update the package information.  After reading a thread on these forums I solved the problem by deleting a line in /etc/apt/apt.conf:
```
Acquire::http::Proxy "false";
```
Can someone please explain how this solved the problem?
Is there a graphical method for performing this task?  I looked at the Synaptic preferences before and after performing this task and didn't notice any differences. :confused:

---

