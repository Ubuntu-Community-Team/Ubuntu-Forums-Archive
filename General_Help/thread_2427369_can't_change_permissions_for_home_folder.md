---
title: "can't change permissions for home folder"
date: 2019-09-21
forum: General Help
---

### Post by tshis on 2019-09-21
Hey friends!
How to I change the permission for my home folder back to read & write?  Some how it got changed to read only.

---

### Post by yancek on 2019-09-21
How did you determine this was the case?  Did you simply to try to create a file in your /home directory or create a file there and fail or did you get a message indicating it had been changed to read-only.  If it is the 2nd option, you may need to do a filesystem check.

---

### Post by TheFu on 2019-09-21
Probably used a GUI file manager with root. Not knowing how some permissions were changed is scary.  They don't magically change on their own.  Someone, probably with root access had to do something.

Unfortunately, if the OP is so new as to need to ask the question, it is likely that other basic knowledge is needed to fill in gaps before the solution can be correctly handled.  It is also unlikely that the top-level of HOME was modified, but some subdirectories, so there really isn't a single answer to the question.

[http://linuxcommand.org/tlcl.php](http://linuxcommand.org/tlcl.php) - start by reading and working through the first 250 pages to get passed beginner level. This teaches Unix/Linux in the correct order, because skills build on prior skills.  Learning in order is important.

In order to provide correct help, and ensure I don't do more harm than good, I'd want to see the file and directory permissions for the problem files and directories.  **ls -al filename** A path to the file might be needed, as well as the permissions for the directory where the file resides.

---

### Post by SeijiSensei on 2019-09-21
```

cd /home
sudo chown username:username username -R
sudo chmod u+rwx username -R

```
That will restore ownership to user "username" on all files and directories in /home/username and grant that user full privileges on all those files and directories.

---

### Post by TheFu on 2019-09-21
```

sudo chown -R    $LOGNAME:$LOGNAME     $HOME 
sudo chmod -R    u+rwX      $HOME 

```should be a little safer.  There could be problems it won't fix and it might break a few things. Hard to tell. It won't fix the group or "other" level permissions.

For what each command does, there is a manpage.  **man chown**  ; **man chmod**  to view them.

---

### Post by SeijiSensei on 2019-09-21
I usually assume the user knows his or her username and doesn't need something like $LOGNAME. Maybe I'm being unreasonably optimistic.

---

