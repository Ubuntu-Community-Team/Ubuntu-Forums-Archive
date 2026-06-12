---
title: "VMware and black screen"
date: 2007-02-05
forum: General Help
---

### Post by banditti on 2007-02-05
I kicked off the XP install and got through the license agreement, partitioning, etc.  Then at the reboot part, it goes black and never comes back. Thoughts?

---

### Post by banditti on 2007-02-05
I figured it out.  It is a permissions issue.  I moved my vmware folder from /home/user/vmware to /user/vmware and all is well.

---

### Post by banditti on 2007-02-08
As a clarification, I did a couple of things at the same time and the following actually fixed it.  I can't remember which post I found it in to give credit.

sudo chown -R yourusername:yourusername vmware

---

