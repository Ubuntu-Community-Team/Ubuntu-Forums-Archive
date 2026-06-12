---
title: "[SOLVED] Changing User Name via Properties?"
date: 2007-11-03
forum: General Help
---

### Post by drs305 on 2007-11-03
My old computer will now be used solely by another person in the family and I want to change the main (i.e. first) username. Can I simply go to System, Admin, Users and change the name in Properties and leave everything else the same?   That seems too easy...

I know I could make a new username but I think I've read that only the first username created can execute admin privileges via sudo. Additionally, the files used will all be essentially the same so there isn't really much reason to duplicate them in another user profile.

Advice or inputs?

Thanks.

---

### Post by ecschiel on 2007-11-03
You can change the name, but i would advice that you don't for privacy issues. The better approach is that you create a new user with admin rights (just select administrator in the profiles settings when creating the new user), and if you wont be using your accont again, delete all your files under the home directory

---

### Post by mahousaru on 2007-11-03
Changing the name shouldn't be a problem apart from the person's name saved in applications. In terms of files (which is what the whole os is made of) every thing is done in terms of uuid and guid, which is a unique number on that system for the user and group.  For example if we don't think too much about non linux file systems, the first user created is 1000:1000 so if you saved things under a user called flobby on your pc on a removable drive and then plugged it into my pc the files would show up as my first user which is called mahousaru.

The user's real name, user name and group names are stored in

/etc/group
/etc/passwd

```

mahousaru:x:1000:1000:Mahou Saru,,,:/home/mahousaru:/bin/bash

```

Now the first mahousaru maps my user name to 1000:1000, if I change that to flobby and then look at my home directory, the files would suddenly be owned by flobby.  The numeric owner hasn't changed only the way the OS translates them.  The second Mahou Saru is the real name used by the system.  Good programs should pull the username and real name from the passwd file.

But as ecschiel points out creating a new user is a lot easier as it avoids things like pidgin or firefox which are specific to the user and not taken from this global store.

**Don't mess with the above files unless you are sure you know what you are doing.  You can bork a machine by deleting or adding the wrong entries**

---

### Post by drs305 on 2007-11-03
Thanks for the replies. I didn't realize I could make a new user with administrator rights, so that is what I'll do.

---

