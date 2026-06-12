---
title: "Vim readonly help."
date: 2007-09-11
forum: General Help
---

### Post by coolgreen1 on 2007-09-11
Hi I have a server running ubuntu server edition 7.04 and just installed Vsftpd and needed to configure it so I used Vim to open vsftpd.conf and it says that the file is read only but I can still edit the file so I edit the file and when I go to save it it says I have to put (!) to over ride the read only so I do but then it says  no changes since last write but I just changed the file so I type in the command to get rid of the read only but that did not work I am lost at this point.

Any help would be appreciated.  Thank you.

---

### Post by kellemes on 2007-09-11
You trying to open this file with the correct priviliges?
I mean.. I can imagine it's a root-owned file so you should "sudo vim vsftpd.conf".

---

### Post by coolgreen1 on 2007-09-11
> **kellemes said:**
> You trying to open this file with the correct priviliges?
I mean.. I can imagine it's a root-owned file so you should "sudo vim vsftpd.conf".

That fixed the problem.  Thank you

---

