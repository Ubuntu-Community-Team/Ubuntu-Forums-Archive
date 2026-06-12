---
title: "I want to fsck more often!"
date: 2007-03-27
forum: General Help
---

### Post by PurplePenguin on 2007-03-27
As it is, fsck runs every 30 boots.  As I usually keep my system running for weeks at a time (and usually only reboot after video drivers freeze my system!), I would prefer to run fsck upon boot more often.  In fact, I would absolutely love it if it would check my drives each time I booted (or maybe every 2 or 3 times at the most).

From what I've read (usually people have the opposite problem and don't want to run fsck), I need to modify my fstab.  0 at the end of the line which mounts a partition turns off fsck, right?  So what are my other options?  What do 1 or 2 do?

EDIT: My searching has taught me that "The 6th column is a fsck option. fsck looks at the number in the 6th column to determine in which order the filesystems should be checked. If it's zero, fsck won't check the filesystem."  So it looks like I'm barking up the wrong tree with the fstab.

---

### Post by 23meg on 2007-03-27
You can use tune2fs to adjust the fsck frequency.

```
sudo tune2fs -c 10 /dev/hdaX
```

will make fsck run at every 10 boots.

---

### Post by dcstar on 2007-03-27
> **23meg said:**
> You can use tune2fs to adjust the fsck frequency.

```
sudo tune2fs -c 10 /dev/hdaX
```

will make fsck run at every 10 boots.

And you can also set a period, like once a day, once a week etc. etc.

---

### Post by PurplePenguin on 2007-03-28
Thanks, guys!  I haven't seen this command before.  Ubuntu Forums comes through for me again! :)

---

