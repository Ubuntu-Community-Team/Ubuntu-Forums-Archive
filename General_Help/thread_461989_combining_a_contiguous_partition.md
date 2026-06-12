---
title: "combining a contiguous partition"
date: 2007-06-02
forum: General Help
---

### Post by cbrukin on 2007-06-02
I was wondering if it is possible to combine a contiguous partition into one, I have a c drive with xp home installed and next to it I have an empty partition.  I am running xp home on the c drive . I have read that in ubuntu there is a tool that you can use to do this but I cannot get past the point where I install from the iso image cd. If anyone can help it would be greatly appreciated.

---

### Post by merlinus on 2007-06-02
You can install gparted from Application/Add Remove, but I have found that using the gparted live cd works better.

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

-merlin

---

### Post by cbrukin on 2007-06-02
I have been doing some investigating over the internet and the reason I decided to try ubuntu was that someone mentioned this to me 

" if you are new to linux with ubuntu. It is small and a snap to install if you want to dual boot, it has a simple gui based installer that works off the live cd, also it because of its simplistic gui you can get it to repartition your hard disk quite easily as it just about walks you through it. " 

 I was afraid to proceed because after booting from the cd I did not see anything like this.

---

### Post by merlinus on 2007-06-02
Once the live cd version is up-and-running, look for an Install icon on your desktop near the top left.

Click on it and the installation process will begin.

After answering a few questions, you will get to the partitioning screen.

But....  if you are running windows and want to keep it, before installing do this:

Defrag your windows drives several times.  If there are errors, the defrag tool will let you know how to try to fix them.

Set virtual paging to zero.  This can be set back to around the same size after installing ubuntu.

Be sure NOT to select "Use Entire Disk" (or something to that effect) when partitioning.  There is a guided option that will use the free space by re-sizing your windows partition and creating the ones necessary for ubuntu.

Good luck!

-merlin

---

### Post by cbrukin on 2007-06-03
thanks you will try this and let you know if it works

---

