---
title: "Grub won't work after repartion of free space"
date: 2007-12-21
forum: General Help
---

### Post by Zophixan on 2007-12-21
Hiya, I just repartitioned my dual boot system of vista and linux, and now grub doesn't work! The files are the same I think? but I'm not too familiar with linux so maybe I lost some files? What would be the best way to fix this? Preferbly without a reinstall :-(

---

### Post by p_quarles on 2007-12-21
No, you probably don't need to reinstall the whole thing, you just need to reinstall GRUB. You can do this with the live disk, or you can use a tool specifically designed for that job:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

---

### Post by Zophixan on 2007-12-21
Hi, thanks for the swift response. I have a live boot disc which I'm using now, how would I reinstall grub? (I'm a major linux newbie!)

---

### Post by p_quarles on 2007-12-21
> **Zophixan said:**
> Hi, thanks for the swift response. I have a live boot disc which I'm using now, how would I reinstall grub? (I'm a major linux newbie!)
Here's a link to the how-to on that topic:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by Zophixan on 2007-12-21
Thanks a bunch :-)

---

### Post by Zophixan on 2007-12-21
Ok my windows partition works but my linux parition says, "Resize inode not valid". and "Unexpected inconsistancy run fsck manually". When I do run fsck manually, it asks an option, yes or no, and I have to answer yes to alot of them! Is there anyway to speed this up?

---

### Post by p_quarles on 2007-12-21
Not that I know of. Let fsck run its course, and it may be able to repair the problem for you.

---

### Post by Zophixan on 2007-12-21
Oh, what I meant was, is there a thing such as fsck -a where I can let it run a automatic manual check? I don't fancy the idea of pressing y 100000 times, easier to reinstall probabily! Thanks :-)

---

### Post by p_quarles on 2007-12-21
> **Zophixan said:**
> Oh, what I meant was, is there a thing such as fsck -a where I can let it run a automatic manual check? I don't fancy the idea of pressing y 100000 times, easier to reinstall probabily! Thanks :-)
Well, yes. 
```
fsck -a
```
will attempt to repair all filesystems without asking. The man page lists this as potentially dangerous, so you may end up having to reinstall anyway.
```
fsck -n
```
will run the check without asking, but will not attempt to repair anything, so it's a bit more safe.

Didn't realize you were getting *that* many y/n prompts. ;)

---

### Post by Zophixan on 2007-12-22
Whoops looks like my entire filesystem is dead, reinstall it is!

---

### Post by p_quarles on 2007-12-22
Bummer. Yeah, sometimes repartitioning can bork things. I'm guessing from the "!" that you've already got everything backed up, though. ;)

---

