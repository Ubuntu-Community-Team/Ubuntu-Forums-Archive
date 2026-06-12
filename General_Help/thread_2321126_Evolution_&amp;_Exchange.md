---
title: "Evolution &amp; Exchange"
date: 2016-04-20
forum: General Help
---

### Post by ttito on 2016-04-20
Hallo Forum!

Is there anything happen with Exchange in Evolution?
Since 2 days ago, all was OK.
Now my Password wont function in Evolution Ubuntu 15.10.
In Outlook everything was OK?

Thanks!

---

### Post by QIII on 2016-04-20
*Moved to **General Help***

Hello!

Forum Feedback & Help is for support specifically related to the operation of the Forum software.

---

### Post by badowskiryan on 2016-04-22
I am having the exact same issue that began at the exact same time as yours.

Similar bug reports:
[https://www.mail-archive.com/debian-bugs-dist@lists.debian.org/msg1413122.html](https://www.mail-archive.com/debian-bugs-dist@lists.debian.org/msg1413122.html)
[https://bugzilla.redhat.com/show_bug.cgi?id=1327072](https://bugzilla.redhat.com/show_bug.cgi?id=1327072)

I'll post the workaround / solution here if I come across it.

---

### Post by badowskiryan on 2016-04-22
Found a solution based on the info here:
[https://bugs.launchpad.net/ubuntu/+source/evolution-mapi/+bug/1571854](https://bugs.launchpad.net/ubuntu/+source/evolution-mapi/+bug/1571854)

It requires the removal of Samba, which is used for file and printer sharing. A recent security upgrade in Samba broke some functionality. You might have some issues if you rely Samba for other things. I do not.

**Here's what worked for me:**
- Open a terminal *CTRL+ALT+T*
- Type *sudo apt-get remove samba* and press Enter
- Follow the prompts to remove Samba and the related packages
- Open Evolution, and you should be able to connect

Hope that helps.

---

### Post by s-breedveld on 2016-04-22
Wow, THAT worked! Looking at it for days.

My history: stopped working after 14.04 LTS update. Decided to upgrade to 16.04 LTS today, but did not solve anything :/

Thanks!

> **badowskiryan said:**
> Found a solution based on the info here:
[https://bugs.launchpad.net/ubuntu/+source/evolution-mapi/+bug/1571854](https://bugs.launchpad.net/ubuntu/+source/evolution-mapi/+bug/1571854)

It requires the removal of Samba, which is used for file and printer sharing. A recent security upgrade in Samba broke some functionality. You might have some issues if you rely Samba for other things. I do not.

**Here's what worked for me:**
- Open a terminal *CTRL+ALT+T*
- Type *sudo apt-get remove samba* and press Enter
- Follow the prompts to remove Samba and the related packages
- Open Evolution, and you should be able to connect

Hope that helps.

---

### Post by ttito on 2016-04-22
Best Tipp ever!!
Remove Samba and all is OK!
Then reinstall it and all works!

Thanks to all :-)

---

