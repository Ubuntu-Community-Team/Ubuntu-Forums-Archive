---
title: "Question on file undeletion and file removal"
date: 2007-03-07
forum: General Help
---

### Post by CaptSaltyJack on 2007-03-07
I have a few questions on file deletion.

#1, I know that when you delete a file, it just wipes access to it but in many cases the data can still exist on the HD, and if you want to securely remove a file, you should use "shred -u".  My question is, if I've just been using 'rm' to remove files, is there a command I can run to wipe out all deleted data, leaving just zeroes in the empty spaces?  In other words, if I've removed my entire mp3 collection, though that data might still exist on the HD, I'd like to run a command that would wipe all of that data.

#2, is there an undelete command?

---

### Post by NT4usB on 2007-03-07
#1
[http://www.jetico.com/bcwipe_unix.htm](http://www.jetico.com/bcwipe_unix.htm)

I've used the windows version. I installed it on my Edgy box but haven't run it yet.
ymmv.

#2 I dunno...

---

### Post by CaptSaltyJack on 2007-03-07
Cool.

What about an undelete command?  Surely there's something for Linux.. especially running on a journaled filesystem.

---

