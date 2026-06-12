---
title: "How to mount a network drive? (smb)"
date: 2007-02-06
forum: General Help
---

### Post by battleroyalex on 2007-02-06
I have a folder on my network
```
smb://smalltop/Linux
```

This is how I share between my windows and linux computers. Is there a way to mount this in linux to make it one click access?

---

### Post by battleroyalex on 2007-02-06
edit: never mind my smb4k is acting up, but I still want to mount it somehow

---

### Post by ^rooker on 2007-02-06
You can use "Places/Connect to Server" to create a desktop-icon for that ressource.
Simply select "samba" as type and enter the required information.


If you want to "mount" that share into a directory somewhere in your filesystem, you can use "mount -t smbfs ....." to do that (see [smbmount-documentation]("http://www.linuxcommand.org/man_pages/smbmount8.html") about parameters)

---

