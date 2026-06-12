---
title: "someone monkeying with groups"
date: 2008-03-04
forum: General Help
---

### Post by lvm on 2008-03-04
After a reboot I found out that sudo doesn't work. The reason was that I was no longer a member of admin group, to fix it I had to boot from a CD which is a nuisance. Then I noticed that sound doesn't work and that was because I was removed from audio group as well. And from some other groups, in fact I belonged to only one group I've added recently. The question is: who did it and how can I avoid it in future? I was logged in for about a month, so quite a lot happened, a number of updates installed - I cannot figure out who is the culprit - maybe you can help?

---

### Post by PeterJS on 2008-03-04
You said the only group the account was in was a group you recently added, did you add your account to that group by hand in the command line? If you don't use the -a (for append) flag the command line tools will happily overwrite all your group memberships for only the new one.

---

### Post by lvm on 2008-03-04
Frankly speaking I don't remember how I did it, but usually I just edit /etc/group and gshadow manually

---

