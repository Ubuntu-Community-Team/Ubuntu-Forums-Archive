---
title: "rsync, --delete, and new/deleted files"
date: 2008-03-20
forum: General Help
---

### Post by vav on 2008-03-20
I use the same data folders on two computers which connect over ssh. I'm trying to set up rsync to keep the folders in sync.

Everything seems to work except deleting files... suppose I create a file on machine #1 (m1) and then go to machine #2 (m2)
now if I use rsync without --delete, and use it first one way and then the other, it'll copy over the new file from m1 to m2 -all good so far.

But if I'm using --delete, and if I first rsync from m2 to m1 (in an automated script, say), then it'll delete my newly created file :(

So suppose I dont use --delete.

But I delete a file from m1. Now if I use the automated script again, it'll re-copy the file on to m1 from m2!

Is there a smarter way to do the sync? Maybe a program which maintains a journal to sync so that deleted and created files automatically get updated? or is this possible with any rsync options?

---

### Post by qpieus on 2008-03-20
From what you describe rsync is working as designed. The trick with the -delete option is that it is dependent on what direction you are rsyncing, as you are finding out.

Check out unison.

[http://www.cis.upenn.edu/~bcpierce/unison/](http://www.cis.upenn.edu/~bcpierce/unison/)

I think this will work for you. I haven't used it, but I've read lots of posts from people who have and it seems to work well. Its in the ubunto repos.

---

### Post by vav on 2008-03-20
Thanks... that seems to be a good option.

Haven't got it working yet, am still trying.

---

### Post by vav on 2008-03-20
As soon as I figured out that I had to install unison on BOTH machines, it started to work ](*,)
:roll::roll::roll:

---

