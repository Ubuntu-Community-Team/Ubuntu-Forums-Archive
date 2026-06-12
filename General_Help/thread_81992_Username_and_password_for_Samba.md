---
title: "Username and password for Samba?"
date: 2005-10-25
forum: General Help
---

### Post by Mizzou_Engineer on 2005-10-25
I use my computer in a home network with Windows computers. I can see their shares and access them just fine. They can see my shared folder but when they try to access it, they get a "Connect to localhost.localdomain" dialog box that asks for a name and password. My username and password do not work. 

Any ideas on how to fix this? I do have the folder set read-write and browseable.

---

### Post by mgor on 2005-10-26
does this happens when you're trying to access the samba shares from windows?
since windows 2000 and above (if i'm not misstaken) needs encrypted passwords samba needs it's own passwd file. add a user with smbpasswd.
```
sudo smbpasswd -a user
```

you have to have a "normal" (useradd) user before using smbpasswd, and it's probably best settings the same password with smbpasswd as with passwd (haven't tried diffrent).

---

### Post by manicka on 2005-10-26
[http://www.ubuntuforums.org/showthread.php?t=76647](http://www.ubuntuforums.org/showthread.php?t=76647)

---

