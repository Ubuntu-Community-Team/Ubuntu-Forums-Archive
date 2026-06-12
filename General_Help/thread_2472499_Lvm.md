---
title: "Lvm"
date: 2022-02-28
forum: General Help
---

### Post by shane_faulkinbury2 on 2022-02-28
I installed Ubuntu 20.04.4 and forgot to install LVM with it.  Is there anyway to install it without starting over.   Meaning install it after the OS is fully installed?

---

### Post by TheFu on 2022-02-28
Not "in place".

An install takes 15 minutes.  Restoring the backups of files/settings (assuming you didn't do images) takes 15 minutes, tops.  Feed in the list of manually installed packages and install those - that's 10min.  So, in about 35-45 min, you have a system that has LVM and "feels" like your old system with all the data, settings, and programs from before.  There are lots of high-level posts for making backups like this and a few for how to restore them. They aren't cookbooks, because every system is a little different.

---

### Post by mIk3_08 on 2022-03-01
> **shane_faulkinbury2 said:**
> I installed Ubuntu 20.04.4 and forgot to install LVM with it.  Is there anyway to install it without starting over.   Meaning install it after the OS is fully installed?
I always agree with TheFu its because your plan seems so impossible. I prefer you have to install it back again from the start and configure those things that you want it to be. so Good Luck and cheers.

---

### Post by shane_faulkinbury2 on 2022-03-01
I figured as much for a clean running OS.  No biggie, I have everything backed up on my external and I might fix a problem I have with my video files not showing.

---

### Post by TheFu on 2022-03-01
> **shane_faulkinbury2 said:**
> I figured as much for a clean running OS.  No biggie, I have everything backed up on my external and I might fix a problem I have with my video files not showing.

Post a clear question about file permissions in another thread and someone can probably help. I doubt LVM has anything to do with it, since LVM isn't a file system. It is a volume manager.  In that new question, specify the file systems involved. If you don't know - say so.  Also, showing the mount options would be good.  Again, if you don't know, say so.  And lastly, please show facts - **ls -al** output for the directory and files that go missing.

---

