---
title: "Help with Kernel log - swap and memory errors (?)"
date: 2012-12-23
forum: General Help
---

### Post by CharlesA on 2012-12-23
Hello,

I've noticed a bunch of junk in my kernel log that seems to relate to memory management.

This seems to have started on the 20th, but it's been consistently occurring. Judging from the timestamps, it looks like it started originally when the workstations were backing up files to the server (which started at 00:30), but it isn't really consistent. After googling some of the messages, it seems to point to a memory problem, but the machine has 16GB of RAM and so far has only used around 2-3GB when these messages occur. The only change that occurred prior to this happening was an upgrade of apparmor.

I've attached the messages I have been getting in the kern.log

So far I haven't seen any other messages about this for the 23rd, but I want to know how to track down what is causing this, even though the server is running fine (no lock up/no freezing/no crashing).

Running 3.2.0-30-generic on Ubuntu 12.04 server x64.

Any help is appreciated. Thanks!

EDIT: I had to upload the log files in a zip cuz the one from Dec 21st was 244KB, which is disconcerting.

---

### Post by Doug S on 2012-12-23
Note before: Actually, I have no clue but... I have only ever seen you help others. I don't think I have ever seen you ask a question, so I thought I should try to help.
 
I wonder if your memory has become so fragmented, that even tough there is lots free, the allocation request fails. From what I have read, this would be a temporary situation. Although they are difficult to understand (at least for me), the fragment details are listed, on a per event basis, in the log files. Perhaps compare with manual listings during more idle periods.
 
Some references:
[http://lists.openwall.net/netdev/2011/11/28/25](http://lists.openwall.net/netdev/2011/11/28/25)
[https://lkml.org/lkml/2012/3/10/128](https://lkml.org/lkml/2012/3/10/128)
[http://stackoverflow.com/questions/4863707/how-to-see-linux-view-of-the-ram-in-order-to-determinate-the-fragmentation](http://stackoverflow.com/questions/4863707/how-to-see-linux-view-of-the-ram-in-order-to-determinate-the-fragmentation)
 
One notible difference is "Tainted" verses "Not tainted", which I am not sure how much to worry about. Also, one reference refers to network stuff and "gro", and I do see that in your logs in the call trace, but not sure how relevant it is.

---

### Post by dino99 on 2012-12-23
as i see your virtualbox installation has to be blamed: seems to need more ram  ;);)

start by purging the actual version, then install the latest virtualbox released a few days ago. (oracle ppa)

---

### Post by Doug S on 2012-12-23
I have been continuing to search and read, and I agree with dino99.
I found a couple more good references:
 
[http://www.linuxsmiths.com/blog/?p=527](http://www.linuxsmiths.com/blog/?p=527)
[http://lime-technology.com/forum/index.php?topic=23222.0](http://lime-technology.com/forum/index.php?topic=23222.0) (<<< Edit: Better reference.)
 
Edit: I am not sure I agree that you need to purge and re-install the vbx though. If it were my system I would want to prove, with certainty, the root cause of the problem and the solution. I would first reduce the minimum free memory (see "Better reference" above) to make the problem worse, then increase it to reduce/eliminate the problem. I would repeat the reduce/increase cycle at least twice (i.e. at least over 4 nights), to know for sure. All of this without rebooting, and knowing that there actually is no bad side effect of the issue.

---

### Post by CharlesA on 2012-12-23
> **dino99 said:**
> as i see your virtualbox installation has to be blamed: seems to need more ram  ;);)

start by purging the actual version, then install the latest virtualbox released a few days ago. (oracle ppa)

Hrm, I installed the latest virtualbox version 4.2.6 on the 19th, and that seems to be when this started happening. That's probably to blame then.

I have just been upgrading it but I will try a fresh install and see if the problem clears up.

> **Doug S said:**
> I have been continuing to search and read, and I agree with dino99.
I found a couple more good references:
 
[http://www.linuxsmiths.com/blog/?p=527](http://www.linuxsmiths.com/blog/?p=527)
[http://lime-technology.com/forum/index.php?topic=23222.0](http://lime-technology.com/forum/index.php?topic=23222.0) (<<< Edit: Better reference.)

Thanks for the links.

> 
Edit: I am not sure I agree that you need to purge and re-install the vbx though. If it were my system I would want to prove, with certainty, the root cause of the problem and the solution. I would first reduce the minimum free memory (see "Better reference" above) to make the problem worse, then increase it to reduce/eliminate the problem. I would repeat the reduce/increase cycle at least twice (i.e. at least over 4 nights), to know for sure. All of this without rebooting, and knowing that there actually is no bad side effect of the issue.

Good point. The server in question is up to like 80 days of uptime so far with no problems except this one. I just checked the kern.log now and there are no error messages (yet).

For the time being, I'm going to purge and reinstall VBox and see if that does any good. Can't hurt right?

Alright, I just purged vbox and all dependencies, and reinstalled it then started a VM (with 2048MB memory allocated).

I'll see if it freaks out again tonight and check the memory usage again. As of now it says:

```
charles@Thor:~$ free -m
             total       used       free     shared    buffers     cached
Mem:         15905      15699        206          0        584      12121
-/+ buffers/cache:       2992      12912
Swap:        16234          0      16234

```

---

### Post by CharlesA on 2012-12-28
Alright, it's been about 4 days since I reinstalled VBox and so far there aren't any more messages in the kernel log.

Marking this as solved.

---

