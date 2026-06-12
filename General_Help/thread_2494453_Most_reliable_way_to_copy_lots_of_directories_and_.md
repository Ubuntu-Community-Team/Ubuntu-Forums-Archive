---
title: "Most reliable way to copy lots of directories and files."
date: 2024-01-17
forum: General Help
---

### Post by Advait on 2024-01-17
Ubuntu 22.04. Newbie here. I've got lots of files and directories on an external USB C connected HDD. About 1TB of files and directories. They all reside in one directory on the HDD.

I want to copy them to an empty directory on my main drive (in my /home directory). What is the most reliable way to do this? 

So far I've explored using the cp command and GRsync. Which one do you think is more reliable? Reliable means it can reliably copy lots of files and directories over a USB C connection.

Better options?

My internal drive is a 2TB nvme.

I have no NAS and no RAID and no home network. ONLY one single AMD laptop. And a stack of external HDDs used for backups.

I'm a newbie so won't use rsync.

---

### Post by dragonfly41 on 2024-01-17
Perhaps add LuckyBackup GUI .. but rsync is in the engine room.
Don't forget to try "dry run" option which simulates, before committing.
You can also see the command line which LuckyBackup compiles.
You can also create multiple profiles for incremental workflow.

---

### Post by ajgreeny on 2024-01-17
> **Advait said:**
> <snip>
I'm a newbie so won't use rsync.
Is this because you are a new user and don't like the command-line and using terminal commands?
It's not nearly as difficult as you may be thinking and could be very useful in many other situations.
However why not have a look at **grsync** which is a simply GUI for rsync and may make you life easier, at least to begin with!

---

### Post by Advait on 2024-01-17
I think I found the solution. I'm using the FreeFileSync GUI app. It took a few minutes to figure out how to set the FFS restore parameters, but I did a small test and it worked good. I&#8217;m now restoring my user files from the external drive back to my internal drive. And the FreeFileSync GUI is pretty good. Great for a newbie like me!

---

### Post by Advait on 2024-01-17
> **ajgreeny said:**
> Is this because you are a new user and don't like the command-line and using terminal commands?

**[[Yes, My old brain is no longer able to learn and remember a bunch of cryptic command line parameters.]]**

It's not nearly as difficult as you may be thinking and could be very useful in many other situations.

**[[Yes, you're correct, but my other commitments currently don't allow me to take time and properly learn something like rsync.]]**

However why not have a look at **grsync** which is a simply GUI for rsync and may make you life easier, at least to begin with!

**[[I have looked at Grsync. It looks pretty good. But I found something even better, see my earlier post.]]**

text

---

### Post by Advait on 2024-01-17
It's interesting, backing up the 1TB of files from my internal nvme to an external USB connected HDD takes about 35hrs.

Restoring the same 1TB of files from the external USB connected HDD to my nvme takes about 2hrs. 

Time to get some ssds for my external backups! :)

---

