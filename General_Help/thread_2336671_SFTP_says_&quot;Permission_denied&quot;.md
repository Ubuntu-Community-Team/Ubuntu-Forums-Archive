---
title: "SFTP says &quot;Permission denied&quot;"
date: 2016-09-10
forum: General Help
---

### Post by KingNeil on 2016-09-10
SFTP was previously working for me, using Ubuntu 14.04.

I created a "snapshot" using the DigitalOcaan hosting service.. Then wiped the server.. Then restored the "snapshot".

Everything is working, except SFTP doesn't work.

When I log in with SFTP

sftp root@IP

it simply says, "Permission denied, please try again"

My password is the same password as before.... It's just suddenly stopped working.

What do I do..?

---

### Post by TheFu on 2016-09-10
Look at the logs?
Contact digital ocean support?

Never allow remote connections via root. Always use ssh-keys and a different account, then use sudo, only as necessary.

Can you ssh in - i.e. is sftp the only issue?  What about scp?

Always check the logs.

---

