---
title: "Can't switch user from local to NIS user"
date: 2007-09-13
forum: General Help
---

### Post by bullish on 2007-09-13
Hello,

I am logged in as a local user on my machine. I usually log in with my NIS account, but it is much faster if I use my local account. When I do need to access an NFS share that has permissions only for my NIS account, I would like to su to my NIS account but am not sure exactly how to do so.

root@localmachine:~# su <nis-account>
Cannot execute /bin/csh: No such file or directory

Any ideas? Thanks.

---

### Post by McNils on 2007-09-13
/bin/csh is missing. Install c-shell or make a soft link. Well, you might need to make that link anyway since csh can be installed in /usr/bin.

---

### Post by bullish on 2007-09-13
Yes. I installed csh and that fixes the issue. I will likely create a symlink back to bash. Is that valid? I have permissions to do what I need now. Thanks...

RESOLVED.

---

