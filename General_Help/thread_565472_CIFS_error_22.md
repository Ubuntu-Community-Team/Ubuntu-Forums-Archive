---
title: "CIFS error 22"
date: 2007-10-02
forum: General Help
---

### Post by yurtboy on 2007-10-02
Had this problem for about an hour and want to post it here so others do not.
3 servers, two worked fine one did not.
Even though CIFS seems to be there to replace smbfs you still need to install apt-get install smbfs
then it works.
Otherwise mount -a etc all got error 22

So hope this helps anyone who gets stuck.
This was on edgy may apply to others.

---

### Post by msack on 2007-10-18
I was having the same problem and it turn out I didn't have the smbfs package installed, which has the mount.cifs client.

---

