---
title: "Phantom File Share"
date: 2008-03-10
forum: General Help
---

### Post by Son of Silas on 2008-03-10
Hi,
A while back I shared some directories on a Gutsy PC on my LAN. I noticed this evening that if I browse it's IP address from a different PC I can see a shared directory that is no longer actually shared on it.

Any Ideas how I can delete that share?

---

### Post by SpaceTeddy on 2008-03-10
can you please specify "share" ? do you mean you had samba create some shares ? and if so, did you remove the shares from samba, or simply delete the directory.

if you do not know what i am talking about, please post the output of the following commands

```
cat /etc/samba/smb.conf
smbclient -L //localhost
```

the second might ask for a password - just press enter and it should work :)

---

