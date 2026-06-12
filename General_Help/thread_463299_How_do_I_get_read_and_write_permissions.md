---
title: "How do I get read and write permissions?"
date: 2007-06-03
forum: General Help
---

### Post by IceDigger on 2007-06-03
I have a second hard drive I put in the computer and when I moved files over to it I can't get full read and write permissions.  When I right click on the drive icon and click on permisions it says root and I can't change anything.

Is there a simple way to fix this without using the command line?

---

### Post by tronica on 2007-06-03
```
sudo chmod 777 /whatever/here
```

that should do it.

---

### Post by IceDigger on 2007-06-03
That doesn't work for the subdirectories or subfiles.

---

### Post by Kuraudo on 2007-06-03
To change owner
```
sudo chown -R <username> /media/disk
```

You can also try a
```
man chown
```
or
```
man chmod
```

---

### Post by strabes on 2007-06-03
you should also change the GROUP associated with files/folders. ```
sudo chown -R username:username /media/disk
```

---

### Post by IceDigger on 2007-06-03
Thanks a bunch guys.

Is there any way to do it without going to a command line though?

---

