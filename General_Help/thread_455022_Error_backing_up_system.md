---
title: "Error backing up system"
date: 2007-05-26
forum: General Help
---

### Post by nami on 2007-05-26
Hello

I have "just" backed up my installation using

[http://ubuntuforums.org/showthread.php?t=81311](http://ubuntuforums.org/showthread.php?t=81311)

The command line I used was:

> 
tar cvpzf backup.tgz --exclude="/media/My Book" --exclude=/home/nami/Desktop/backup.tgz /

/media/My Book is my external HDD which I did not want to include in the backup, and obviously I did not want to include the tgz file being created.

but when the process finishes I get the following message in the terminal window:

> tar: Error exit delayed from previous errors
root@nami-desktop:/home/nami/Desktop#

Does this mean I can't back up my system?

---

### Post by nami on 2007-05-26
Ignore this post, I just noticed the following in the link above:

> At the end of the process you might get a message along the lines of 'tar: Error exit delayed from previous errors' or something, but in most cases you can just ignore that.

---

