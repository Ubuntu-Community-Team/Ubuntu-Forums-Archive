---
title: "What fixes for hanging starts on ECrypt swap partitions?"
date: 2016-12-05
forum: General Help
---

### Post by bcschmerker on 2016-12-05
I recently had to disable CryptSwap on the Hot Rod gPC due to hangs during startup.  Specifically, on a string of attempted boots on 4 December 2016, ECryptFS startup hung on at least one partition, stalling the entire OS startup in the process; the Debug terminal readout showed the hang along the following lines:
```
[<---->] A start job is running for dev-mapper-cryptswap3.device [??m??s / No limit]

```This never completed short of a reboot.  My suspicion involves the failure of automatic cipher keysetting attempting to start at least one (which one varies per boot attempt) of the five 8 GiB swap partitions.  The root, Boot, User, Option, Variable, and Home partitions are not affected by this issue.  How does one go about troubleshooting inconsistent dev-mapper-cryptswap*n*.device performance?

**Update:**  Researching the problem at Launchpad&#8482;, I learned that the hit-and-miss cipher key generation may be due to an [issue with systemd that causes a hang-on-attempted-shutdown after suspend/resume](https://bugs.launchpad.net/ubuntu/+source/systemd/+bug/159045).  Similar enough to my hang-on-attempted-shutdown when aborting startup with a hung cryptswap, to await [better information on how a misbehaving systemd could stall ecryptfs](https://answers.launchpad.net/ubuntu/+question/404663).

**Update 2:**  I found that Phoronix® relayed a fix notice from the LinUX Kernel Project concerning a bug filed 2009 for the B-Tree File System that could be a possible root cause for the ECryptFS on account of inaccurate reads.  Standing by for more information on the bug....

---

