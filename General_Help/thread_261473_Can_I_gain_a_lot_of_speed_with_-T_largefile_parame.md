---
title: "Can I gain a lot of speed with -T largefile parameter"
date: 2006-09-20
forum: General Help
---

### Post by bugmenot_user on 2006-09-20
I created an ext3 partition of 12 GB for my cd and virtual harddisk image files. I formatted this partition with -T largefile parameter. So it's block size is too big (1 Mb!!)and it can only store 12000 files. Now, I want to store small files in this partition, too. 

Will there be a spectacular increase in my performance compared to an ext3 with a smaller block size if I use the partition as it is? So, should I look for other solutions by keeping the partition as it is.(for example creating a disk image in the same partition and mounting this as if it is a normal disk.). Or, should I reformat the partition with a normal block size (It's not a problem to reformat the partition, because there isn't much file in it.;)

---

### Post by kidders on 2006-09-20
Hi there,

There are lots of other factors that influence real filesystem performance, besides the filesystem itself. It is, for instance, entirely possible that your tuning has had no impact on overall performance at all! Equally, you might find that you get a very noticeable performance hit by undoing your optimisation ... it's hard to tell without actually trying it :-( You know how it is ... there can sometimes be a bit of a gap between theory and fact.

It is however generally true that filesystems that are good with big files are bad with small ones, and vice versa. If you are looking to push your PC as hard as you possibly can, and squeeze every last CPU cycle out of it, then here's my opinion -- for what it's worth!

Rule 1, as you've already done is to try not to use "general purpose" filesystem architectures that are ... well ... equally bad at doing everything!

Rule 2 is to experiment with multiple filesystems. ReiserFS, for instance, claims to hold overwhelming performance advantages over its competitors, when it comes to small files.

Rule 3 is to use your RAM. There's no reason not to mount parts of your home directory into memory. As you might imagine, it'll read/write unbelievably quickly!

Consider the following, as a "for instance":

Say your /home/<username> contains directories called "Movies", "Documents" and "src". There's no reason not to mount an ext3 partition with a ridiculous block size at /home/<username>/Movies, a standard ReiserFS one at /home/<username>/Documents, and put "src" into RAM, so when you're compiling things from source, it happens in a heartbeat. ReiserFS features very sturdy corruption protection, so your documents stay safe, and your movies will copy like lightning, and never skip.

This may seem overcomplicated, but, once it's done, you won't have to think about it any more. I guess the question is whether such highly tuned filestorage is (a) worth the bother, and (b) actually makes the difference it's intended to, in practice.

**Edit:**

One of the cardinal rules in system tuning is to completely eliminate CPU cycle wastage related to I/O operations. Try this little experiment. Open a terminal window and run **nice top -d 1**. Now, force the window on top of all your others, and carry on working. Keep an eye on the third line from the top of the output, specifically the CPU usage indicator called "wa". In simplistic terms, this is an indicator of the amount of CPU time being wasted, waiting on I/O operations to complete. If this number is high, the kind of filesystem tuning you are (quite bravely!) attempting is one of the ways you can try to reduce it.

Imagine paying double price for a CPU with 2 or 3 hundred extra megahertz, only to discover that it's all being thrown away on a badly tuned filesystem or crappy RAM!

I hope this helps!

---

### Post by bugmenot_user on 2006-09-21
First, thanks for your post. Now, I'm starting to write.

> **kidders said:**
> Try this little experiment. Open a terminal window and run nice top -d 1. Now, force the window on top of all your others, and carry on working. Keep an eye on the third line from the top of the output, specifically the CPU usage indicator called "wa". In simplistic terms, this is an indicator of the amount of CPU time being wasted, waiting on I/O operations to complete. If this number is high, the kind of filesystem tuning you are (quite bravely!) attempting is one of the ways you can try to reduce it.

I tried this. I have two ext3 partitions. The first one has big block size and the second one has "normal" block size. I copy a big file (~250 Mb) from reiserfs partition to ext3 partitions. Wasted CPU time and copying time was nearly equal. (By the way, wasted CPU time was  ~65-75% during copying!! I think it is too bad :( 
And then, I copy this files from ext3 partitions to reiserfs part. Wasted CPU time was same.(65-75%). Copying time wasn't equal. Copying from the small block size one was 4-5% fast. :razz: Therefore, I think I reformat this partition with smaller block size :D . These tests aren't covering all cases but I think it is enough for me.

> **kidders said:**
> There's no reason not to mount parts of your home directory into memory
What about power loss?

> **kidders said:**
> put "src" into RAM, so when you're compiling things from source, it happens in a heartbeat.
Great idea! But, I don't know how can I do this. I guess I should  use -t tmpfs for filesystem and tmpfs for device name?

> **kidders said:**
> I hope this helps!
Yes, it helps! :)

I tried and I saw using big block size doesn't increase my performance and doesn't have any advantage. Using small block size doesn't have any drawbacks and it has some advantages. I will reformat my partition :)
Thanks for your advices! (and sorry for my bad English :))

---

### Post by kidders on 2006-09-21
Hi again,

First of all, there's **nothing** wrong with your english! Are you not a native speaker?!

When doing copy experiments, it is not wise to involve more than one filesystem type ... this can drastically affect the outcome ... how do you know ReiserFS isn't 100 times faster at reading than writing, for instance? In addition, CPU cycle wastage will always be _HUGE_ during copy operations, since physical storage devices are *extremely* slow (comparitavely speaking). Wastage during "normal" use is a much more reliable indicator.

At any rate, as long as **you** are happy you're making the right choices, that's all that matters. Linux is designed so that you can have the system you want, and not the one someone else thinks you should have :-)

In response to your query about power loss, RAM-based filesystems are not always very practical. On occasion though, people are happy to take risks, given the potential pay-off. Storing /tmp in RAM can be very smart, for instance.

Anyhow, I hope all this has helped answer your original question!

---

