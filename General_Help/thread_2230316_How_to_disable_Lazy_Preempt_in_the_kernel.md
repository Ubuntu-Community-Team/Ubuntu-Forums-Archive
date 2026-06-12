---
title: "How to disable Lazy Preempt in the kernel"
date: 2014-06-18
forum: General Help
---

### Post by Thomas_James on 2014-06-18
Hello,

I'm relatively new to Linux and working on getting a real-time kernel up and  running for robot applications. I'm on Ubuntu 14.04, using kernel  3.14.3 and the 3.14.3-rt5 real-time patch. Also using x86-64. 

There's a known error where the whole system crashes under some load when lazy preempt is enabled. This has happened to me a few times now. My question is:

How do I disable lazy preempt? 


I read to add "NO_PREEMPT_LAZY" to the end of  /sys/kernel/debug/sched_features, but when I try to do that (using " ~$ sudo  vim /sys/kernel/debug/sched_features "), upon trying to save and exit  (:wq) I get the following error: 

"/sys/kernel/debug/sched_features"
"/sys/kernel/debug/sched_features" E667: Fsync failed
WARNING: Original file may be lost or damaged
don't quit the editor until the file is successfully written!
Press ENTER or type command to continue 


If someone could help me get past the vim 'Fsync failed' or disable lazy preempt in another way, I would greatly appraciate it. 

Thank you!

-Tom

---

