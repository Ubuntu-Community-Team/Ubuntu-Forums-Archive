---
title: "group permissions confusion"
date: 2008-03-20
forum: General Help
---

### Post by FallingFrog on 2008-03-20
I apologize in advance if this is a stupid question... but, I am having trouble getting any kind of group permissions to work in ubuntu.

Here's a sequence of commands that reproduces the problem.
```

sudo mkdir test_dir
sudo chgrp users test_dir
sudo chmod 774 test_dir/
cd test_dir
```

And what I get is:
```
bash: cd: test_dir/: Permission denied
```

If I try this:
```
touch test_dir/test.txt
```

I get:
```
touch: cannot touch `test_dir/test.txt': Permission denied
```

Even though when I run ls:
```
drwxrwxr--   2 root users  4096 2008-03-20 13:13 test_dir
```

Now, I know for a fact that the user I was logged in as when entering these commands was in group users,  Here's the line from cat /etc/group:
```
users:x:100:sean,root
```

In fact it's the primary group for that user.  So why can I not enter test_dir?  If I set the permissions to 777, everything works as expected.  Try it on your machine.  (You get the same behavior when the owner is some other user than root.)

---

### Post by Het Irv on 2008-03-20
I am not sure but would the fact that you are using sudo to 'elevate' you to root cause any problems?

---

### Post by iris-n on 2008-03-20
You have to log out and back in for your group changes take effect.
Just Ctrl+Alt+Backspace to kill the GUI and try again.

---

### Post by FallingFrog on 2008-03-20
Thanks!  Rebooting fixed the problem.  I wonder if it would be a good feature request to make group changes take effect right away.

---

### Post by Het Irv on 2008-03-20
I don't know if that is possible, espically if you are changing the group you are in.

---

### Post by iris-n on 2008-03-20
Actually there were horrible problems with the system allowing to change a user's id while logged, i think it has been corrected already.
Trust me, it's a lot safer to wait to the user to relog, think about a running procces that is suddenly stripped of a user that granted it privileges to do what it must. Isn't cute?

---

### Post by Het Irv on 2008-03-20
Those programs exist, ya know?  One of the many reasons I switched to Linux.

---

### Post by FallingFrog on 2008-03-21
> **iris-n said:**
> Actually there were horrible problems with the system allowing to change a user's id while logged, i think it has been corrected already.
Trust me, it's a lot safer to wait to the user to relog, think about a running procces that is suddenly stripped of a user that granted it privileges to do what it must. Isn't cute?

Hmm, good point, I figured there was probably a reason for that behavior.

---

