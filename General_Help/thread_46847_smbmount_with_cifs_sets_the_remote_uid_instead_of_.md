---
title: "smbmount with cifs sets the remote uid instead of the client"
date: 2005-07-06
forum: General Help
---

### Post by moment on 2005-07-06
I have an account on a SuSE server where my home directory is shared with Samba. On my Ubuntu I have the same username as my remote server but with a different uid. When I mount my home directory using:
```
sudo mount -t cifs -o username=ho1,password=secret //mysever/ho1 /media/ho1
```
it mounts them with the uid of my server account instead of my home uid so I can only access them with the root account. Using uid and gid doesn't make any difference either. This problem is only with smbmount. Does anybody have any idea to get around this annoying problem?

best regards
Hamid

---

### Post by m.aicardi on 2005-07-19
You can give a look here:

[http://lists.samba.org/archive/smb-clients/2005-May/000572.html](http://lists.samba.org/archive/smb-clients/2005-May/000572.html)

It talks about smb and uid/gid.

Bye.

Marco

---

### Post by acehigh on 2005-12-24
Same problem of you.
I've read the article, but my kernel is newer than those and indeed has the same problem.

Any help?

---

