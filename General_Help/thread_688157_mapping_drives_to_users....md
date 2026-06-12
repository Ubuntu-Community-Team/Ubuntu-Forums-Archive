---
title: "mapping drives to users..."
date: 2008-02-05
forum: General Help
---

### Post by Mia_tech on 2008-02-05
is there a way in ubuntu to map drives to the users over the network at log on time... lets say with samba for example

---

### Post by ayoli on 2008-02-05
If I have understood right, you need to create the users on your machine:
```
sudo useradd -g users -s /bin/false username
```
Then add the users to samba database and give them a password
```
sudo smbpasswd -a username
```
(replace *username* with the name of each user)

Then create a share for each user in your /etc/samba/smb.conf
```
[share_name]
    comment = a comment
    writable = yes
    valid users = username
    path = /path/for/this/user
    create mode = 0660
    directory mode = 0770
```

---

### Post by Mia_tech on 2008-02-05
question: does the command above, push the share created in samba when the user log on from the remote machine?..... what I'm trying to understand is for example in windows, you can run a .bat file that resides in netlogon share on the server which in turns push the network maps among other things... is there a way to do this in ubuntu?... hope I explain myself

---

### Post by ayoli on 2008-02-05
> **Mia_tech said:**
>  for example in windows, you can run a .bat file that resides in netlogon share on the server which in turns push the network maps among other things... is there a way to do this in ubuntu?
Yes, but, I dunno renember how.
Maybe, reading docs like this could help : [http://www.faqs.org/docs/samba/toc.html](http://www.faqs.org/docs/samba/toc.html)

---

