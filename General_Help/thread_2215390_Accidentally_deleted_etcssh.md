---
title: "Accidentally deleted /etc/ssh"
date: 2014-04-06
forum: General Help
---

### Post by kpmaddenuk on 2014-04-06
Hi,

Trying to be tidy I've deleted my /etc/ssh directory and the files in it by mistake.

I tried to recreate by uninstalling and then reinstalling ssh but this doesn't recreate the directory or the files. The mkdir is easy but is there somewhere that I can get the files from?

Cheers - SD

---

### Post by steeldriver on 2014-04-06
Did you reinstall both ssh packages (**openssh-server** as well as **openssh-client**)?

There may also have been a /etc/ssh/ssh_import_id file provided by package **ssh-import-id**

Interestingly it looks like no package provides a **file **/etc/ssh/sshd_config - it gets written on-the-fly by the openssh-server postinstall **script**. If reinstalling openssh-server doesn't recreate it for you, I guess you could try 

```
sudo dpkg-reconfigure openssh-server
```

EDIT: obviously you only need to fix the server files if you actually had the SSH server installed in the first place

---

### Post by kpmaddenuk on 2014-04-06
That did it. Thanks.

Easy whenyou know how isn't it. :)

---

