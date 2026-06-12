---
title: "Forgot login password of a Virtual Installation"
date: 2007-12-07
forum: General Help
---

### Post by Ted_Smith on 2007-12-07
If I create an install of Ubuntu via a Virtual Machine and forget my login password (which was also the same as the sudo password, for arguments sake), is there anyway to recover it? I understand the recovery console creates a random password even if the user does not set one so I don't think that will work.

---

### Post by Ramorous on 2007-12-07
A clear cut way to do it is, load up a live CD, create an account with Sudo powers and copy over the /etc/group, /etc/shadow, /etc/passwd files to the VM's root directory. You may need to mount them if not mounted automatically.

---

### Post by aysiu on 2007-12-07
> **Ted_Smith said:**
> If I create an install of Ubuntu via a Virtual Machine and forget my login password (which was also the same as the sudo password, for arguments sake), is there anyway to recover it? I understand the recovery console creates a random password even if the user does not set one so I don't think that will work.
Yes. The same principle for recovering a forgotten password applies to both real and virtual Ubuntu installations.

Instructions are here:
[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

---

