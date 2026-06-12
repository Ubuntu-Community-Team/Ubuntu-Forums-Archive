---
title: "sshfs filesystems no longer appearing"
date: 2012-10-30
forum: General Help
---

### Post by dzn2 on 2012-10-30
Ubuntu 12.04
OpenSSH v5.9
sshfs v2.3

This is a minor annoyance, but at the beginning of October we ran some OS updates and since then the sshfs filesystems are no longer appearing in the output from the df and mount commands. Although greping the ps output for sftp shows they are still mounted.

Looking in the update log, sshfs and openssh were not updated. So what update may have have caused this change in behaviour and is anyone else seeing something similar?

Thanks for any help.
Dave

---

