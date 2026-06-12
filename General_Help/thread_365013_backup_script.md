---
title: "backup script"
date: 2007-02-19
forum: General Help
---

### Post by tronica on 2007-02-19
I need to backup the contents of a harddrive to server on the network, i want to write a bash script to do so. But i'm not real sure where to start, Basicly i just want to copy all the contents off that drive, to the server. But can i make it so it won't overwrite whats there? I'm also planning on setting it up with cron. any ideas.

---

### Post by aysiu on 2007-02-19
Try *rsync* or *rdiff-backup*.

For starters, read this:
[http://www.psychocats.net/ubuntu/backup](http://www.psychocats.net/ubuntu/backup)

---

