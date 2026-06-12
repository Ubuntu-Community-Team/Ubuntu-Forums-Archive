---
title: "Apparmor is preventing cups-pdf from working"
date: 2013-08-24
forum: General Help
---

### Post by apollothethird on 2013-08-24
Can someone help me to override apparmor's block of cups-pdf?  After a lot of research it appears that the problem is that my home directory is in a linked filesystem.

Every time I try to output to the PDF I get a dmesg error:

```

[ 1840.832973] type=1400 audit(1377351531.230:47): apparmor="DENIED" operation="mkdir" parent=1097 profile="/usr/lib/cups/backend/cups-pdf" name="/home/users/l/j/ljames/PDF/" pid=11755 comm="cups-pdf" requested_mask="c" denied_mask="c" fsuid=0 ouid=0

```

Thanks in advance for any suggestions on this.

-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3.com/~ljames](www.apollo3.com/~ljames)

---

