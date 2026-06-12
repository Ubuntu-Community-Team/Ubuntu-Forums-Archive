---
title: "Samba part fully open and part password protected"
date: 2014-08-06
forum: General Help
---

### Post by iclestu on 2014-08-06
Hi,

Is it possible to have a samba file share set up with anonymous read/write access but then to password protect & make non-browsable a certain sub-directory tree?

Also - i am struggling to get normal anonymous access to work. I have this in /etc/samba/smb.conf:
```

[PublicShare]
writable = yes
path = /home/<me>/Shared/
public = yes
guest ok = yes
guest only = no
guest account = nobody
browsable = yes
```

and I can successfully navigate and read from the directory from a windows machine on the network but cannot write to it. i get a permissions error.

I added the account 'nobody' with the command:

```
sudo adduser nobody sambashare
```

not sure what i am missing here?

Any ideas?

---

