---
title: "How to prevent boot from pausing when a drive has failed"
date: 2016-06-16
forum: General Help
---

### Post by jrmymllr on 2016-06-16
Using 14.04.

While hundreds of miles from home, I SSHed into my system only to find one of the drives had failed (not the OS drive obviously).  I foolishly rebooted it thinking it was worth a shot.....but I was never able connect again.

When I got home it turns out it was stuck on the message "the disk drive for [share] is not ready yet or not present" and it was asking if it should Skip or do a manual mount.  Had it defaulted to "skip" things would have turned out better.

Lesson: never remotely reboot unless absolutely necessary.

Is there a way to default to Skip should this happen again?

---

### Post by Impavidus on 2016-06-16
This may be of interest: [http://unix.stackexchange.com/questions/53456/what-is-the-difference-between-nobootwait-and-nofail-in-fstab](http://unix.stackexchange.com/questions/53456/what-is-the-difference-between-nobootwait-and-nofail-in-fstab)

---

### Post by jrmymllr on 2016-06-16
Great, that's it!  Thanks

---

