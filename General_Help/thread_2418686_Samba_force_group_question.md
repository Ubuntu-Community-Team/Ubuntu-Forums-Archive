---
title: "Samba force group question"
date: 2019-05-09
forum: General Help
---

### Post by donb21 on 2019-05-09
Over the years, I've migrated my smb settings from one version to the next and always had "force user" and "force group" under the share setups...like this:

[home]
 comment = Home
 path = /home
 public = yes
 writable = yes
 create mask = 0660
 directory mask = 0770
 force user = don
# force group = mythtv

On this version, "force group" gave me errors similar to this thread:

[https://www.pickysysadmin.ca/2015/08/27/samba-update-breaks-ad-authentication/](https://www.pickysysadmin.ca/2015/08/27/samba-update-breaks-ad-authentication/)

Removing that line seems to have resolved the problem.  Not sure why I've always had it,or, what it does.  Is that parameter obsolete?

Don

---

### Post by TheFu on 2019-05-09
I don't know. Never used either "force whatever" myself.  We always setup Unix groups and all members for a specific share are in the same group.
For lots of locations, only the [homes] stanza is needed.
```
[homes]
  comment = Home Directories
  hosts allow = 127.0.0.1 172.22.22.0/24  
  hosts deny = 0.0.0.0/0
  browseable = yes
  guest ok = no
  writable = yes
  create mask = 0644
  directory mask = 0755
  valid users = %S

```
Homes is special.

---

### Post by SeijiSensei on 2019-05-10
Force user/group tells Samba to use those credentials when talking with the operating system. I've used them in the past when I was sharing an accounting application to a half-dozen users and wanted all the Linux-level file transactions to take place under a single pseudo-user.  

In your case, there's no obvious reason why you would want Linux to address the /home branch as group "mythtv".   I'm actually a little puzzled as to why user "don" is the owner of /home.  /home should be owned by root:root.  /home/don should be owned by user "don" and by don's primary group.  Usually in Ubuntu those are the same.

---

