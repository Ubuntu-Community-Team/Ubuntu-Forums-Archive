---
title: "Questions about LVM"
date: 2007-04-15
forum: General Help
---

### Post by rogeriovinhal on 2007-04-15
Hi, I am new to LVM, never did anything with it, but read something about it and it may be useful for me.

I have some questions to see if it is save for me to try it with my home partition.

The problem is: I have set a initial space for my home partition, but then I found out that I could use some more space. But I couldn't resize the physical partition. So I did another partition and started to split files in both of them.

But this is a little annoying. I read that I could join both of them with LVM, but I don't know if that's safe for me.

Am I going to lose any data in the partitions?
If I join them in LVM, will my home partition be visible only to the system I did join them?
Are there any performance issues that might make LVM unattractive?
Is it easy to do, and mess-proof for newbies?

Thanks for the help.

---

### Post by viciouslime on 2007-04-15
> **rogeriovinhal said:**
> 
Am I going to lose any data in the partitions?
If I join them in LVM, will my home partition be visible only to the system I did join them?
Are there any performance issues that might make LVM unattractive?
Is it easy to do, and mess-proof for newbies?

Thanks for the help.

As far as I know you will have to wipe out your current home partition to make an LVM one, so yes, you will lose all your data, you can't just convert it. However, if you have somewhere to back it up first this isn't really a problem.

I'm not quite sure what your second question means? If you had say opensuse and ubuntu installed on the computer both would be able to use the LVM partition regardless of which one you set it up with. Does that answer your question? However, in this case, sharing a home partition between two different distros isn't really recommended as it can cause configuration problems since you will likely have different versions of apps accessing their configs in the home directory. It is of course fine to access the home partition from a different distro, I just wouldn't recommend using the same home directory for both distros.

I could be wrong, but from what I have read in the past there can actually be performance increases in using LVM.

In ubuntu... not really. In opensuse however, it is very easy to do, it actually defaults to this if I remember correctly. Ubuntu's partitioner, doesn't allow you to do this though I don't think...


Hope that's of some help, but tbh I haven't really had experience of LVM at all, so it would be good if someone with more experience could try and help you out too...

---

