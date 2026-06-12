---
title: "Moving Application Files to New Partitions"
date: 2007-01-03
forum: General Help
---

### Post by llanitedave on 2007-01-03
Hi, I'm using Kubuntu on Edgy, and have gotten myself into a bit of a problem.

When I installed, I partitioned my two hard drives into several different volumes.  My thought was to use a fairly small volume to hold the root directory, and a larger volume to hold the user and home data.

The problem is that I didn't implement it very well.  For example, Mozilla Thunderbird was installed onto my root partition, as were most of my home directories.  I've run out of disk space, as the mail files have filled it up.

I moved my .mozilla-thunderbird home directory, which includes my saved mail files, to the larger partition, but it broke the links to it.  Now, when I activate Thunderbird, it sends me to the setup wizard, as if I'm a new account.

How can I reconnect the links from the Thunderbird application in the small volume to the data in the large one, so that I have access to my mail without filling up my partition?

And when I've solved that problem, can I use similar techniques for other applications?

Thanks!

---

### Post by bodhi.zazen on 2007-01-03
I am not sure, but do you know how to create a link ?

```
ln -s /new/location/of/.mozilla-thunderbird ~/.mozilla-thunderbird
```

Watch the space between .mozilla-thunderbird and ~/.mozilla-thunderbird

---

### Post by bapoumba on 2007-01-03
> **llanitedave said:**
> 
The problem is that I didn't implement it very well.  For example, Mozilla Thunderbird was installed onto my root partition, as were most of my home directories.
Hi,
is your /home actually on that big partition or in the root partition ?
What is the output to **cat /etc/fstab** ?

---

### Post by llanitedave on 2007-01-03
Thanks for the hints.  I'll be looking that up later today, and I'll let you know what I find.

---

### Post by llanitedave on 2007-01-03
```
ln -s /new/location/of/.mozilla-thunderbird ~/.mozilla-thunderbird
```

Why is it the most dead-simple things are the hardest to remember!?!?!?

Problem solved.  Thanky so much!

---

