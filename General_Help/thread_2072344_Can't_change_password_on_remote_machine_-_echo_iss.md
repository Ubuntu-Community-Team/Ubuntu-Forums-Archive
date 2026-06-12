---
title: "Can't change password on remote machine - echo issue?"
date: 2012-10-17
forum: General Help
---

### Post by AndyCinDallas on 2012-10-17
I've googled myself to death and can't find the answer to this question.

I'm trying to change a user's password (in this case it happens to be the root user as I'm currently playing with Metasploitable installed on a different box for work purposes) - but I don't get an opportunity to enter the password the first time, so it fails.

Using a simple exploit, I get root on the box - awesome. However, here's what I get next:

```
root@metasploitable:/# **passwd root** (I press Enter and immediately get this:)
Enter new UNIX password: Retype new UNIX password:
```

Notice how the new password request and the confirmation are on the same line? That's what I get as soon as I type "passwd root" and press Enter - so I don't get to change the password.

This is what it should look like normally, as you're probably well-aware:

```
root@metasploitable:/# passwd root
Enter new UNIX password: (I type in a new password and hit Enter)
Retype new UNIX password: (I confirm the new password and hit Enter)
passwd: password updated successfully
``` 

I figured it might be an echo issue, but I've done "echo off" and it hasn't resolved the issue. Complicating matters is that I'm running Linux in a VirtualBox VM on my workplace Mac - I don't know enough yet about Mac to know whether that could be part of the problem.

---

