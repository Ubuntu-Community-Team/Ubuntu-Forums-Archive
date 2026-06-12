---
title: "Need Help Please - User Management Broken"
date: 2007-05-30
forum: General Help
---

### Post by knichel on 2007-05-30
I recently upgraded Feisty (May 29 @ 8:30am EST) and now my User Mangement is broken. I get an error about orphaned modules and last upgrade broken...
 
More details at [http://paste.ubuntu-nl.org/23115/](http://paste.ubuntu-nl.org/23115/)

Please Help, I am desparate...

Mike

---

### Post by knichel on 2007-05-30
This issue is resolved.  I am using NIS to handle student logins and the +:::::: at the end of /etc/passwd was causing this problem. I have reported this as a bug to the developers of kde-guidance.

---

### Post by CyberAngel on 2007-09-29
I have the same problem since feisty and now on gutsy after a dist-upgrade.

Can you, or someone else tell me how to solve this?

Thanks!

---

### Post by knichel on 2007-09-29
If you are referring to not being able to manage the users, the only solution I have found is to remove the +:::::: temporarily and while you edit a user then put it back.  Sorry.

---

### Post by CyberAngel on 2007-09-29
> **knichel said:**
> If you are referring to not being able to manage the users, the only solution I have found is to remove the +:::::: temporarily and while you edit a user then put it back.  Sorry.

But my /etc/passwd does not have any +::::::

---

