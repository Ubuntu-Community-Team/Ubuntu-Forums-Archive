---
title: "Database Access Denied - Mythweb"
date: 2007-08-14
forum: General Help
---

### Post by loudestnoise on 2007-08-14
In the process of trying to set up authentication for Mythweb I somehow screwed everything up and now get a  message saying > Database Access Denied

You are most likely receiving this message because you
have failed to configure mythweb's database login info.

Please see .htaccess for instructions.


Here's what I did probably to create this problem. In the process of getting apache authentication and getting frustrated that I couldn't figure it out (I'll save those questions for later) I decided to just remove the editing I had done to the .htaccess file in my /var/www/mythweb folder.  I downloaded a new copy of Mythweb and just pasted over the info to my edited copy.  After that I think is when the Database Access Denied errors came up.  I don't know what was different in my original .htaccess file than the one I copy/pasted, but now it doesn't work.

---

### Post by loudestnoise on 2007-08-14
Is it possible to force a reinstall? I tried just using

```
sudo apt-get install mythweb
```

but since I already had it, it doesn't do anything. If I could start fresh, that might help.

---

### Post by Maybelline on 2007-09-28
If you're still having trouble, the .htaccess file has your database login info in it.  You might make sure that the login info is valid for your mysql setup.

---

