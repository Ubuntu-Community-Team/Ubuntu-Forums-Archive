---
title: "Syncing Two Computers"
date: 2007-05-22
forum: General Help
---

### Post by ericbarch on 2007-05-22
My brother and I want to make backups of each other's data over the Internet every night. We will have 2 hard drives the same size in our Ubuntu servers. Files that are added or deleted on one computer need to be updated on the other, and vice versa. I've looked into rsync, but I'm not exactly sure how that would work with both hard drives having their contents modified. Any suggestions?

---

### Post by fragos on 2007-05-22
Rsync seems to be a favorite of many but I haven't used it personaly.  You might also consider unison which will do a bidirectional incremental update.  I've used it with memory sticks and computers at work and home for my working directory and all synced well.  One of these computers ran a Windows OS and the other Linux.  If you don't have static IPs you will need to get dynamicDNS from a free site like [www.changeIP.com](www.changeIP.com).

---

### Post by ericbarch on 2007-05-22
Unison looks great. Thanks for the help.

---

### Post by pmg on 2007-05-22
I assume each of your have your own directory tree in which your data is stored, so one tree would be backed up in one direction, and the other tree in the other direction.  Rsync could do that - you'd need two rsync commands as each would only move data in one direction.  Rsync has lots of options, but I suspect you want to start by looking at -a (which is the same as -rlptgoD) and maybe -u.  It takes a little time to learn how to use rsync, but it's one of those tools that is well worth the time to learn.

---

### Post by ericbarch on 2007-05-22
Well the issue is that data may be added/removed on both systems, so there needs to be a program that knows where it was deleted and if it should be removed on the other system or if new data was added and it needs to be copied to one system.

---

### Post by fragos on 2007-05-23
If the synching directions is in question unison give the user the opportunity decide.  I'm not familiar with rsync but I would think it has a similar option.

---

