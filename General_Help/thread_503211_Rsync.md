---
title: "Rsync"
date: 2007-07-17
forum: General Help
---

### Post by hockeypfef on 2007-07-17
What I want to do is use rsync to back up a folder to an external drive.

I would like to keep 30 days worth.

For example:  I have backups of June 1 - June 30.  Once July 1 comes along, I want to keep June 2 - July 1 and delete June 1, and so forth.  

Any ideas how I can accomplish this?

---

### Post by mitch.c on 2007-07-18
You might consider rsnapshot, this provides an automated incremental backup using rsync. It's easy to configure. You can find it in the universe repository.

---

### Post by HermanAB on 2007-07-18
Rsync itself cannot do that, but tar can.  See 'man tar' and the '-N' option.

Otherwise, you can probably use 'find' and execute 'rsync' from that, but it will be a little tricky to figure out.

Cheers,

Herman

---

### Post by amac777 on 2007-07-19
Hi, here is a great tutorial that explains how to use rsync, mv, and cp to do exactly what you described and more. For example, it describes how to make sure the last 30 days worth of snapshots don't take 30 times the storage space - it only needs to store the changed files. 

[http://www.mikerubel.org/computers/rsync_snapshots/](http://www.mikerubel.org/computers/rsync_snapshots/)

Hope it helps.

---

