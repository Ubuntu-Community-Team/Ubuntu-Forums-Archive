---
title: "Very high IOWAIT (process jbd2/sda2-8)"
date: 2015-11-01
forum: General Help
---

### Post by childintime on 2015-11-01
Recently my Ubuntu 14.04.03 LTS is almost unusable, especially after I wake up from suspend. It becomes so slow and unresponsive I cannot perform any actions for like 20 minutes or so until it calms down. I also can't listen to music because it stops every 20 seconds for a few seconds.

I noticed IOWAIT is always very high during slowdown, and iotop shows that the process which has the highest IOWAIT usage is [B]jbd2/sda2-8

[/B]I googled "high iowait", and tried several tools, but I can't seem to find the solution for this. It started happening few weeks ago and I system is almost unusable anymore.

---

### Post by tgalati4 on 2015-11-01
Make sure the power cable is plugged securely into the drive.  Otherwise, look at the SMART parameters of the disk drive.  It could be failing.

---

### Post by IanBal on 2016-01-04
You may be faced with the same problem I ran into.  I filed a bug report against Ubuntu, bug number 1473948 [https://bugs.launchpad.net/ubuntu/+source/nfs-utils/+bug/1473948](https://bugs.launchpad.net/ubuntu/+source/nfs-utils/+bug/1473948) which seems to have not yet been examined.  Maybe the information in my report will help you further.

---

### Post by g1g133 on 2016-01-10
I'm having the same problem and it's driving me crazy, the system just randomly gets unusable for minutes due to the jbd2 process swamping IO at 99%. It seems to be especially bad after a suspend.

I also was running 14.04 LTS and this problem started out of the blue after a kernel update sometime in December. I went back to the previous kernel but the problem didn't go away.

 Unfortunately I can't remember exactly which kernel versions they were as a couple of weeks ago I did a fresh install and upgraded to 15.10 hoping that would fix it but no, still the same random freezes, though I seem to remember the 14.04 kernel version I went back to (so the one before the problem started) ended with 16.

I did a drive SMART check from a live USB drive and it says that the drive is OK, not sure what to do next.

---

