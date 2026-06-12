---
title: "cannot burn DVD beyond 1 gigabyte"
date: 2007-12-23
forum: General Help
---

### Post by kornelix on 2007-12-23
When I upgraded from 7.04 to 7.10 my DVD file backup program stopped working. The problem is very strange: the burned DVDs are readable up to 1.00 GB (1024 MB) and after this all data is garbage. The ISO file directories are fine, and all files below 1 GB can be accessed normally. All files above 1 GB are garbage even though the directory entries are present. I found the very file where the problem began - the data is good up to a point and then - zeros. 

I am using growisofs which uses genisoimage. I first suspected these programs and experimented to verify. I moved the execution files for these programs, and my program which uses them, from 7.04 to 7.10. The 7.04 execution images ran OK on 7.10 (as expected), and produced the same error! On 7.04 these same execution images work perfectly. 

So I am left with the conclusion that the problem is in the kernel or the installed libraries, which seems really strange.

Before filing a bug report, I thought I would try this to see what feedback, if any, I can get. I can find lots of DVD burning bugs in these forums, but nothing that clearly matches this problem.

---

### Post by kornelix on 2007-12-25
Update: re-installing Ubuntu fixed the problem. It will remain a mystery.

---

