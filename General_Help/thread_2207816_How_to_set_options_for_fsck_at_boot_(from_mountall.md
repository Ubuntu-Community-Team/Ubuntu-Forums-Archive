---
title: "How to set options for fsck at boot (from mountall)"
date: 2014-02-25
forum: General Help
---

### Post by narcisgarcia on 2014-02-25
I've set this option at /etc/default/rcS
FSCKFIX=yes

And set periodic checks for an old hard disk:
$ sudo tune2fs -c 30 /dev/sdb1

But I need to fsck makes an action like this when programmed:
$ fsck -cy /dev/sdb1

How can I set (mountall?) to use the option -c when the boot process includes fsck revisions?

---

### Post by TheFu on 2014-02-25
**sudo touch /forcefsck** only works for the / partition.
Don't know how to force a "YES" though.  I suppose you could write a tiny script to run fsck every X times/days and put it into /etc/init.d/ to force a check at the next boot using /forcefsck. I haven't tried this.

I didn't know about the /etc/d...rcS .... interesting. The comment in the version of that file here seems to imply only a "YES" for fsck at boot, not that it will actually run fsck every time.

Interesting need. Google found this: [http://askubuntu.com/questions/151025/how-can-i-make-fsck-run-non-interactively-at-boot-time](http://askubuntu.com/questions/151025/how-can-i-make-fsck-run-non-interactively-at-boot-time) which explains more about  FSCKFIX=yes 

Sorry, I dont know more.

---

