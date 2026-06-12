---
title: "umask seems to vary by user"
date: 2014-02-11
forum: General Help
---

### Post by evaarties on 2014-02-11
I have an Ubuntu system with two users, if I create a file or folder with the first user, it becomes like this:

```

-rw-rw-r--  1 ernst ernst      0 feb 11 22:48 z_a_file
drwxrwxr-x  2 ernst ernst   4096 feb 11 22:48 z_a_folder/

```

This is as expected since the umask 0022 becomes 0002 in Ubuntu as the group id equals the user id.

But, when I do the same with my other user, I get this:

```

-rw-r--r--  1 susan susan     0 feb 11 22:50 z_a_file
drwxr-xr-x  2 susan susan  4096 feb 11 22:50 z_a_folder/

```

As you can see, the group has no write permission. What can be the difference? Both users are created on this system.

Entry in /etc/passwd:

```

ernst:x:1000:1000:Ernst,,,:/home/ernst:/bin/bash
susan:x:1001:1001:Susan,,,:/home/susan:/bin/bash

```

Entry in group:

```

ernst:x:1000:
susan:x:1001:

```

Groups for Ernst:

```

ernst adm cdrom sudo dip plugdev fuse lpadmin sambashare media

```

Groups for Susan:

```

susan adm sudo lpadmin sambashare media

```

This guy seems to have the same problem, but no solutions has been posted to his question: 

[http://serverfault.com/questions/452088/umask-seems-to-vary-by-user](http://serverfault.com/questions/452088/umask-seems-to-vary-by-user)

What can be wrong?

---

### Post by TheFu on 2014-02-12
Groups: Login users to the physical machine get different groups vs non-login users or remote users. This is to protect local users from remote user jokes.
Also, could ernst be in the sudoers?

umask: If you want to know the umask for any user, type **umask**.  Yes, these can be changed per user.

If you create two new users, exactly the same --- userA, userB, then I'll bet their umask is identical.

---

