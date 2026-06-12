---
title: "Access denied when trying to mount a SMB share"
date: 2007-11-24
forum: General Help
---

### Post by Thimetolive on 2007-11-24
Hello,

I am trying to access a network share via Picasa. I have read that I need to mount the samba share to be able to see it in Picasa's file browser.

When I try ```
mount -t smbfs //192.168.1.100/Storage /media/Storage -o credentials=/etc/samba/smbusers
```
or several variations of that I always get back 
```
 12089: session setup failed: ERRDOS - ERRnoaccess (Access denied.)
SMB connection failed
```

My smbusers file is setup like
```
username=john
password=doe
```

Any suggestions are appreciated. Be gentle I'm new to Linux!

---

### Post by Thimetolive on 2007-11-25
Anyone?

---

### Post by Thimetolive on 2007-11-25
Solved. I wasn't added correctly as a Samba user.

---

