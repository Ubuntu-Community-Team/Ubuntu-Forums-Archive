---
title: "SOLUTION! - 30 boot filesystem check"
date: 2007-04-22
forum: General Help
---

### Post by musther on 2007-04-22
I've seen a lot of posts over the last couple of years about how annoying it is when you start to boot Ubuntu and then suddenly you realise that you've got to wait for the filesystem check, what if you have to give a presentation, or you need to quickly read an email.  It doesn't matter why you need your computer in a hurry, you just do.

Most people (especially those you should trust) will tell you that disabling the 30 mounts check (while being possible) is not a good idea, and many people have suggested theoretical ways in which this could be handled to make the experience better for the user.

Well I've just finished writing a set of scripts which I call AutoFsck which make the annoyances a thing of the past.

When you log in the system checks how long it has been since you checked your disks, if it has been 25 boots or more you are asked if you want to check your disks.  If you say no, the system will be set up to prevent them being checked at the next boot, but you will again be prompted when you log in.  If you say yes, your disks wont be checked there and then, but rather the system will be set up to check them when you next shut your computer down.

[https://wiki.ubuntu.com/AutoFsck](https://wiki.ubuntu.com/AutoFsck)

I'm not a genius programmer, and writing these scripts took a long time, and a lot of learning and experimenting, but I got there, and I'm very glad to be able to give something to the Ubuntu community.  I'll start working on a Kubuntu (KDE) version soon.

Please do whatever you want with AutoFsck.

One more thing, I think the functionality provided by AutoFsck is something that the Ubuntu Distribution needs, and I'm going to propose it for Gusty, comments are encouraged.

---

### Post by mdurham on 2007-04-22
I think that ctrl-alt-del stops the filesystem check. Try it.

---

### Post by musther on 2007-04-22
It may do, although I'm not sure.  I haven't tried it, but even if it does, an efficient dialogue system and checking the disks on shutdown is a 'nicer' way to do it for the user.

---

### Post by mdurham on 2007-04-22
> **musther said:**
> It may do, although I'm not sure.  I haven't tried it, but even if it does, an efficient dialogue system and checking the disks on shutdown is a 'nicer' way to do it for the user.

That's quite true.

---

