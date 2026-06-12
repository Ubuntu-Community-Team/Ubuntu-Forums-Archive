---
title: "apt-get update and install lock issues"
date: 2006-11-27
forum: General Help
---

### Post by jonesyp on 2006-11-27
I was doing a sudo apt-get update last night, and it was struggling with some of the repositories so I broke out of it.  No each time I do a sudo apt-get update I get this error:

E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

I have looked in system monitor and can find o copies of aptitude or synaptic running.  I have also tried rebooting it and leaving it overnight. Can anyone help please?

Thanks

Peter

---

### Post by steevk on 2006-11-27
There is a temp file that you need to delete. It may even be /var/lib/dpkg/lock ...I can't remember 100%, though.

---

### Post by jonesyp on 2006-11-28
Tried that already, wont let me delete it even with sudo.

---

### Post by steevk on 2006-11-28
What kind of output did it give you?

---

