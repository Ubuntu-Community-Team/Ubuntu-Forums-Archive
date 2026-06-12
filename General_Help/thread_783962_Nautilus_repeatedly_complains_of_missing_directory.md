---
title: "Nautilus repeatedly complains of missing directory"
date: 2008-05-06
forum: General Help
---

### Post by Kumera on 2008-05-06
In my shiny new Ubuntu 8.04, whenever I do a "sudo Nautilus" command from a terminal, in order to access a work directory that Ubuntu has decided ought to be off limits to mere mortals like myself, the resulting Nautilus repeatedly issues an error message: 

** (nautilus:10824): WARNING **: Unable to add monitor: Not supported
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

There is no such directory in my system as /var/lib/samba/usershares , and I am not sure why I might need one, or what I should put into it if I were to create one.  Apart from repeatedly issuing this message, Nautilus seems to work normally.  Is this something I should worry about?

---

### Post by chrisccoulson on 2008-05-06
No need to worry. usershare is a feature of Samba that allows the administrator to delegate file sharing privileges to ordinary users. /var/lib/samba/usershares won't exist unless you have installed Samba server. It is the nautilus-share extension which is looking for this folder.

---

