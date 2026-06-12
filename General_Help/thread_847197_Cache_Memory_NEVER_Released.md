---
title: "Cache Memory NEVER Released"
date: 2008-07-02
forum: General Help
---

### Post by maraschin on 2008-07-02
Hi,

I'm having a strange problem with all my computers that are running ubuntu...
After I do a lot of operations with files (like copy, compilation, etc), anything that makes use of the cache, makes the computer ran out of memory!
Well, I do not get any error! It will just not let me open any new applications...

Here an example that just happen:
I did compile a big project with Maven2 which downloaded a lot of files... Right now I get that my computer is using 72% as cache and 22% by programs... (By the way, I've 3GB of memory in this machine).

All seems fine, at least with the open applications like firefox that I'm using to write this new thread. The problem now is that I can't open any new applications, and that includes a simple terminal window!
Nothing that is not in memory already will start!

Does anyone knows for how long the cache system keeps the allocated memory?
Is there a way to make it release it back?

The compilation has ended for quite some time, all the files have already been written to the disc and I still don't have my memory back...
The only solution is to restart the machine.

I'm having the same problem with other machines that are running ubuntu too. All with 8.04 with the latest updates...

Any suggestions?
Any know Bugs???

BTW, I've been "googling" and searching in the forum but I did not find anything like it...

Regards,

/Carlo

---

### Post by maraschin on 2008-07-02
By the way, I ran free -m in a terminal window that was open before I ran out of memory...

free -m
             total       used       free     shared    buffers     cached
Mem:          3026       2809        217          0        290       1785
-/+ buffers/cache:        733       2293
Swap:         3922          0       3921

---

### Post by rebeldevel on 2008-07-02
That's true. I think Ubuntu should release some cache in a timely fashion, to avoid using swap.

EDIT: by the way, to free up cache memory, run this command:

sudo sh -c "sync && echo 3 > /proc/sys/vm/drop_caches"

---

### Post by maraschin on 2008-07-02
I guess I did not google enough...

I found a "possible" solution...

[http://www.faqs.org/docs/linux_admin/buffer-cache.html](http://www.faqs.org/docs/linux_admin/buffer-cache.html)

The command sync may be the answer but I could not replicate it yet in my tests... it could be that update had crashed but I'm not sure.

I tried to fill up the cache and clean with sync and it seems to work fine. But even when I'd the cache full I still could open applications so I'll have to wait to try this one out when I get the same problem again and see if isn't another problem...

---

### Post by sdennie on 2008-07-02
This can't be a problem with the cache.  Having your otherwise unused memory filled by the cache is a very good thing and dramatically improves system performance.  If your applications need memory, linux will drop pages from the cache to make room for your applications.  I suspect something else is going on here.

---

### Post by Mecharuva on 2008-07-02
> **rebeldevel said:**
> That's true. I think Ubuntu should release some cache in a timely fashion, to avoid using swap.

EDIT: by the way, to free up cache memory, run this command:

sudo sh -c "sync && echo 3 > /proc/sys/vm/drop_caches"

Awesome, I've been looking for this.
I just made a launcher for it on the desktop :]
Many thanks.

---

### Post by sdennie on 2008-07-02
The only thing dropping the cache will do is make your system a lot less responsive.  If you want to avoid using swap while retaining the cache, add the following to /etc/sysctl.conf:

```

vm.swappiness = 1

```

Then run:

```

sudo sysctl -p

```

That change will stick over reboots.

---

### Post by maraschin on 2008-07-02
> **rebeldevel said:**
> That's true. I think Ubuntu should release some cache in a timely fashion, to avoid using swap.

EDIT: by the way, to free up cache memory, run this command:

sudo sh -c "sync && echo 3 > /proc/sys/vm/drop_caches"


Thanks!
The command you sent did the trick!
( sudo sh -c "sync && echo 3 > /proc/sys/vm/drop_caches" )

The scenario this time was that I just downloaded 2 iso files (LinuxMCE) and were using the computer normally to write the CDs, surfing and so on... The cache filled up and I was left without memory to open any new applications...

Kernel automatically releasing cache?
Nop, the swap wasn't even used and it did not released anything from the cache...
About future use of the cache:
Yes, I do want to use the cache now and than but in this scenario cache wasn't important...

---

### Post by sdennie on 2008-07-02
> **maraschin said:**
> Thanks!
The command you sent did the trick!
( sudo sh -c "sync && echo 3 > /proc/sys/vm/drop_caches" )

The scenario this time was that I just downloaded 2 iso files (LinuxMCE) and were using the computer normally to write the CDs, surfing and so on... The cache filled up and I was left without memory to open any new applications...

Kernel automatically releasing cache?
Nop, the swap wasn't even used and it did not released anything from the cache...
About future use of the cache:
Yes, I do want to use the cache now and than but in this scenario cache wasn't important...

Unless you've done something very odd to your machine, it's simply not possible that the cache is causing this.  My guess is that nearly every person posting on this forum would find that if they did a "free -m" they would see that the cache is taking all available memory and yet none of them are having the problems you are describing.  Something else must be going on.  You are certainly free to run your machine however you see fit, but, by constantly dropping the cache, you are doing yourself a disservice.

---

### Post by dnegorov on 2008-11-29
I have the same problem with OpenSUSE 11.0

---

### Post by visualblind on 2012-07-18
I am having a similar problem, but it does start using my swap eventually after a few days of uptime. Gradually day by day it increases until the system swaps itself into an unresponsive state, then I have to reboot. This has happened to me on two separate Ubuntu **server** virtual machines. One running internally on an ESX 3.5 host, the other running in Amazon EC2.

cat /proc/version
Linux version 3.2.0-25-generic (buildd@crested) (gcc version 4.6.3 (Ubuntu/Linaro 4.6.3-1ubuntu5) ) #40-Ubuntu SMP Wed May 23 20:30:51 UTC 2012

cat /etc/debian_version
wheezy/sid

uptime
 13:49:30 up 19 days, 20:14,  1 user,  load average: 0.33, 0.44, 0.40

free -m
             total       **used**       free     shared    buffers     cached
Mem:           491        465         26          0         93        202
-/+ buffers/cache:        169        322
**Swap**:         1715         **14**       1701

This "inconvenience" has caused me to increase the Ubuntu Server EC2 instance to a m1.large instance size just so it does not use swap. From my experience with Ubuntu Server, while virtualized it is a horrible operating system to rely on. If anyone can point me in the right direction or provide some assistance, I would greatly appreciate it.
Thank you,
Travis Runyard

---

### Post by oldos2er on 2012-07-18
Old thread closed.

"If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful."

---

