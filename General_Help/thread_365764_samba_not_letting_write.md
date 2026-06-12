---
title: "samba not letting write"
date: 2007-02-20
forum: General Help
---

### Post by gaillard on 2007-02-20
Hey everyone,

I don't quite understand, I am just using samba to be able to write to an ubuntu drive through windows that I am running in vmware but even though the permissions I believe are correct and the writable tag is set to yes in the smb.conf it still says access denied only when I try to create a file or something in windows.  I have the masks in the smb.conf set to 0700

---

### Post by Koybe on 2007-02-20
Did you create the user correctly? smbpasswd -a user

Give us more information on what's on, show us ls, testparm or anything you'll found usefull?

---

