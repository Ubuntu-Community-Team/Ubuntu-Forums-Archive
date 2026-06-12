---
title: "Backing up /home and all user settings"
date: 2006-11-02
forum: General Help
---

### Post by scooper86 on 2006-11-02
I am wanting to upgrade a computer that has dapper on it and I am unsure on changing my sources.list to edgy. I was wondering if there was a way of backing up /home and all other user specific files and folders then install edgy and simply copy the required files back. Cheers.

---

### Post by aysiu on 2006-11-02
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)
[http://www.psychocats.net/ubuntu/partimage](http://www.psychocats.net/ubuntu/partimage)

---

### Post by garretwp on 2006-11-02
simply do a tar -cvf homebackup.tar /home as sudo and that should copy all the files to a tar image and put that in a safe place. I do my backup script in perl with tar and have restored from it many of times with no issues.

- Garrett

---

### Post by mike41 on 2006-11-02
should /etc also be backed up?

---

### Post by scooper86 on 2006-11-02
thanks for the quick replies, I already know to back up the /home directory i was just wondering if there were any files out side of this folder that contained information on the users such as /etc/groups does and what are these files so i can back them up then restore on a clean install of edgy

---

### Post by scooper86 on 2006-11-03
Please if someone could tell me the location of these files or if its at least safe to upgrade my kubuntu dapper to edgy by changing my sources.list. thanks for the help.

---

