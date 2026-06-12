---
title: "strange home folder"
date: 2014-05-12
forum: General Help
---

### Post by patrickallo on 2014-05-12
I've been toying with ubuntu on a vps, and have only recently noticed that my homefolder is in a strange place.

Concretely, my homefolder is at [FONT=Courier New]/home/username/username[/FONT] instead of the usual [FONT=Courier New]/home/username[/FONT]

Is there any reason for this?
While it doesn't seem to cause any problems, it is surely confusing. Is this something I should (and can) fix?

I have found that I should use this:
```
# usermod -md /my/new/home username
```
but am not sure if I can use it while I'm logged in with the account I'm trying to modify

---

### Post by TheFu on 2014-05-12
Whatever the /etc/passwd says is correct.  PERIOD.  If it is accessible, has UNIX file permissions (i.e. NOT NTFS/FAT), that is all that matters. In fact, the owner doesn't even need to be userid if you want to be mean.

If you want to move it, modify the part of /etc/passwd (or LDAP or x.500 directory) which specifies the HOME, then move it to that location. Only personal scripts that don't use ~/ or $HOME will break. The system stuff doesn't care. Before you logout, connect from a remote system and verify that your login works fine first.  If so, logout, login and everything will be fine.

BTW, there is nothing special about /home .... it can be anywhere and different users can have their individual HOME anywhere.

---

