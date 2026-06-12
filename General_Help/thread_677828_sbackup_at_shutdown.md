---
title: "sbackup at shutdown"
date: 2008-01-25
forum: General Help
---

### Post by ctothej on 2008-01-25
I would like to have sbackup run at shutdown only. I have already configured it using the sbackup configuration gui.

My plan was to create a new shell script in /etc/init.d called 'call-sbackup.sh' and have that script call '/usr/share/sbackup'. call-sbackup.sh:
```
#!/usr/bin/sh
/usr/share/sbackup
```
Then, create symbolic link in /etc/rc0.d to /etc/init.d/call-sbackup.sh:
```
cd /etc/rc0.d
sudo ln -s /etc/init.d/call-sbackup.sh S05call-sbackup.sh
```
Will this work as expected?
Do I need to do anything else?

---

### Post by RemcoBoerma on 2008-05-01
I'd say give it a shot!  I'm in need for something similar, so i will come up with a solution if you run into trouble trying yours. But since it has been a while since your post maybe you already have a working solution? If so, please drop it here.

EDIT: i've added my sollution to [https://help.ubuntu.com/community/BackupYourSystem/SimpleBackupSuite](https://help.ubuntu.com/community/BackupYourSystem/SimpleBackupSuite) maybe this helps anyone with the same question.

---

