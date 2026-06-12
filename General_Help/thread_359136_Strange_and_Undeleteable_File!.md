---
title: "Strange and Undeleteable File!"
date: 2007-02-11
forum: General Help
---

### Post by talen888 on 2007-02-11
Hi, 

In the course of setting up MythTV I've ended up with some very strange and undeleteable files. I'm not sure if this is froma system crash or what, but nothing I can do seems to work. 

One of the files is this:

[FONT="Courier New"]?r--rwxrwT 30719 4294901656 4292853759 4160208780 1970-01-01 09:51 mythtv[/FONT]

I've tried the following to delete it, all as sudo/su:

1) rm -f 
2) delete by inode
3) booted a ubuntu LiveCD and mount the partition

Every time I get this: 

[FONT="Courier New"]rm: cannot remove `mythtv': Operation not permitted[/FONT]

Any tips? Going insane...

n

---

### Post by llamakc on 2007-02-11
Immediately I thought the immutable bit had been set, but it doesn't appear that way. You do have the sticky bit set though. Why not trying to chmod it first? `sudo chmod -t /path/to/filename`

I dunno if that will help to be honest.

---

### Post by talen888 on 2007-02-12
nope, that didn't work:

root@aurora:/var/log# chmod -t mythtv
chmod: changing permissions of `mythtv': Operation not permitted

---

### Post by talen888 on 2007-02-12
Ended up dismounting andrunning e2fsck -f on the drive from a LiveCD - seemed to work so far, no idea how those files got there in the first place.

---

### Post by SeanTater on 2007-02-12
I had a similar problem on an old hard drive of mine.  But there was no sticky bit or anything, just a file I had copied from my backups, that would not delete no matter what I did. rm, mv, cp, chmod, chown, nothing worked.. 
As it turns out the hard drive was about 6 hours from dead. Hint: BACKUP YOUR DATA!

---

