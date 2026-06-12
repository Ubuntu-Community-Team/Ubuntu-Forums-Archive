---
title: "getting mkisofs to backup subdirectories correctly"
date: 2005-08-01
forum: General Help
---

### Post by dninja on 2005-08-01
I'm trying to back up my mp3 collection and want to make an iso of it so that I can burn it.

As it goes over 1 DVD I'm doing it in parts so the first command is:

mkisofs -o disk1.iso a* b* c*

which I would like to cover the following directories:

aaa/aa
aaa/bb
aaa/cc
axx/bb
bb/xxx
etc

the problem with this is that rather than putting the the full directories into the iso I'm getting all the subdirectories in the root, so rather than doing a full backup I'm getting:

/aa
/bb
/cc
/bb (over writing the first one I think)
/xxx

I'm looking for a simple solution where I can specify wildcards and get the subdirectories in the right place. I could write something which parses the directory list and generates a full command line for me but I feel it can be done in an elegant 1 liner.

Can anyone help?

---

