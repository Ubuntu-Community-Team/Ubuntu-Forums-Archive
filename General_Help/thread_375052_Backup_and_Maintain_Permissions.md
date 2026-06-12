---
title: "Backup and Maintain Permissions"
date: 2007-03-03
forum: General Help
---

### Post by Joshua on 2007-03-03
Can anyone tell me how to make a backup of stuff in my home directory so that when I restore everything all the permissions of files will be exactly the same?

---

### Post by taurus on 2007-03-03
[http://www.psychocats.net/ubuntu/partimage](http://www.psychocats.net/ubuntu/partimage)

---

### Post by Joshua on 2007-03-03
Great, that looks much more powerful that I was expecting!!

---

### Post by david_2001 on 2007-03-03
For a cheap and cheerful alternative, tar preserves file permissions:
```
tar cjvf archive_file.tar.bz2 /home/username
```

---

