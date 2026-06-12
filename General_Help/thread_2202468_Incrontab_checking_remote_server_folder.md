---
title: "Incrontab checking remote server folder"
date: 2014-01-29
forum: General Help
---

### Post by Cruth on 2014-01-29
Hi,

I'm currently trying to set up folder sync between 2 servers with unison. I've set up incrontab on server 1 and it's watching my folder for any changes and it automatically runs unison when there's a change.
Now is my question do I need to setup a incrontab on server 2 aswell or can I let server 1 check server 2 for changes throu ssh/sftp. The script needs to run as soon there's a change.

---

### Post by Dave_L on 2014-01-29
The incrontab task is triggered by an I/O event. So my guess is that incrontab would have to be set up on the server on which the I/O event occurs.

---

### Post by Cruth on 2014-01-29
Yes was afraid of that. But I wanted to try to ask to be sure. Thank you!

---

### Post by Dave_L on 2014-01-29
My answer was just a guess. You could set up a simple incrontab task to log events to make sure it really works that way.

---

