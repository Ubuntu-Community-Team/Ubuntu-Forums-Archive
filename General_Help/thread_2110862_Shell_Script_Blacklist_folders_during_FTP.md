---
title: "Shell Script Blacklist folders during FTP"
date: 2013-01-31
forum: General Help
---

### Post by CrusaderAD on 2013-01-31
I have a shell script with the following ftp code:

```
ftp -n $ftpurl <<!
quote user $username
quote pass $password
binary
cd $folders
lcd /home/user
prompt
mget *
quit
!
```

Is there a way to blacklist certain folders or subfolders it grabs? Or a way to whitelist certain folders for downloading?

---

