---
title: "how to  deactivate the anonymous FTP account"
date: 2007-05-23
forum: General Help
---

### Post by ceci123 on 2007-05-23
hi, Greetings,

my first time here. 

i installed ubuntu on my pc...relatively new at this. 

I need to know how do I deactivate the anonymous FTP account. 

thank you.

C.

---

### Post by taurus on 2007-05-23
What ftp server are you running: proftpd, vsftpd, etc.?

---

### Post by ceci123 on 2007-05-23
vsftpd

---

### Post by taurus on 2007-05-23
Edit /etc/vsftpd.conf

```
gksudo gedit /etc/vsftpd.conf
```
and make sure this line in there looks like this, disable anonymous ftp.

```
anonymous_enable=**NO**
```
Save it and reboot.

---

### Post by ceci123 on 2007-05-23
it worked beautifully, thank you!

---

