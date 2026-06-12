---
title: "Network Share mount failures at BOOT using CIFS"
date: 2013-02-25
forum: General Help
---

### Post by lyrrad1989 on 2013-02-25
In our Ubuntu 12.04.1 server environment, our servers mount Windows network shares using CIFS: 

When we reboot the servers they give off the following errors in kern.log:
CIFS VFS: cifs_mount failed w/return code = -6
CIFS: Unknown mount option umask
CIFS VFS: cifs_mount failed w/return code = -6
CIFS: Unknown mount option umask
CIFS VFS: cifs_mount failed w/return code = -6
CIFS VFS: cifs_mount failed w/return code = -11
CIFS VFS: cifs_mount failed w/return code = -6
CIFS: Unknown mount option umask

I also receive the following error in /var/log/kern.log:

CIFS VFS: default security mechanism requested. The default security mechanism will be upgraded from ntlm to ntlmv2 in kernel release 3.3

Not sure if these errors are related.

Upgraded the Kernel to version 3.3 and did not find any remedy for the share mounting failures, other then eliminating the errors regarding the CIFS and Kernel version in kern.log

Was just wondering if anyone else had encountered this issue, and do you have any suggestions on how to combat this problem?

I am also wondering if this is bug or could there just be a syntax error?

---

