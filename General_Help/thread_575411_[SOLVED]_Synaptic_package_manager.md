---
title: "[SOLVED] Synaptic package manager"
date: 2007-10-14
forum: General Help
---

### Post by bskafh on 2007-10-14
hi, 
i am seeing these errors when i try to update the system or open the synaptic package manager 

E: Dynamic MMap ran out of room
E: Error occurred while processing gnome-terminal (NewFileVer1)
E: Problem with MergeList /var/lib/dpkg/status
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.

i have no clue what this means. Please any help?

---

### Post by wormser on 2007-10-14
I found the following quote [here]("http://jaqque.sbih.org/kplug/apt-pinning.html").

> **E: Dynamic MMap ran out of room**

You may find that you receive an error like the following:

E: Dynamic MMap ran out of room
E: Error occured while processing sqlrelay-sqlite (NewPackage)
E: Problem with MergeList /var/lib/apt/lists/ftp.us.debian.org_debian_dists_woody_contrib_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.

This is caused because apt's cache is too small to handle all of the packages that are included with stable, testing, and unstable. This is also very easy to fix. Add the following line to /etc/apt/apt.conf

APT::Cache-Limit "8388608";



---

### Post by strabes on 2007-10-14
To make it easy, just run this command:```
gksudo gedit /etc/apt/apt.conf
```Then add the following line to the end of the file:> APT::Cache-Limit "8388608";Save the file and exit.

---

### Post by bskafh on 2007-10-14
i cant file /etc/apt/apt.conf 

i can only find a folder named apt.conf.d, when i ran the commands it created a new text file with the name apt.conf 

anyway its still giving me the same error. any ideas?

---

### Post by wormser on 2007-10-14
> **bskafh said:**
> i cant file /etc/apt/apt.conf 

i can only find a folder named apt.conf.d, when i ran the commands it created a new text file with the name apt.conf 

anyway its still giving me the same error. any ideas?

This [blog]("http://valery.bgit.net/blog-en/2006/11/13/apt-get-e-dynamic-mmap-ran-out-of-room/") has more info on the issue.  Try the number listed in the blog and if that does not work then read the comments.  It looks like there are other numbers you can use if the default one given does not work.  Then try running sudo apt-get update.

---

### Post by bskafh on 2007-10-14
Thanks a lot, your a life saver. at first, for some reason i though i might have a bad sector, because i thought i read some where that this might be caused by a bad sector. just for general info, is there a way to check for bad sectors? how can i derangement the disk using ubuntu? thanks a lot again guys.

---

### Post by wormser on 2007-10-14
I am not sure how to fix bad sectors.  I think fsck is the program you want to use but I did not see anything in the man page about sectors.  You should mark this thread as resolved and create a new thread with the new issue.  You will get a lot more responses.  Also post your resolution so somebody else who runs across this thread will be able to find the answer easily.

Update:  Just post what worked for you.

---

### Post by bskafh on 2007-10-15
what do you mean post my resolution?

---

