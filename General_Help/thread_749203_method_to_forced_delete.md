---
title: "method to forced delete"
date: 2008-04-08
forum: General Help
---

### Post by kjman83 on 2008-04-08
kjman83@guinness:~$ rm -Rf /etc/ndiswrapper/bcmwl5
rm: cannot remove `/etc/ndiswrapper/bcmwl5/14E4:4311:1375:103C.5.conf': Permission denied


kjman83@guinness:~$ rmdir /etc/ndiswrapper/bcmwl5/
rmdir: failed to remove `/etc/ndiswrapper/bcmwl5/': Permission denied
kjman83@guinness:~$ 


I want to delete folder
but I can't delete the files.. How can I remove these files?

---

### Post by sisco311 on 2008-04-08
Put sudo in front of the command to get superuser privileges.

```
sudo rm -rf ...
```[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by kjman83 on 2008-04-08
Thank you very much
Muito bem

---

