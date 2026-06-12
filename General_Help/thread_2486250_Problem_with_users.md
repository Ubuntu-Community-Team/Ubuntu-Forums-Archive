---
title: "Problem with users"
date: 2023-04-24
forum: General Help
---

### Post by pbaro on 2023-04-24
Hello there!, I have the main admin account, but I had to create 2 new users, one with admin privileges and other with standar privileges. The problem is that the new user with standar privileges if I have to install anything in Ubuntu Software it asks me for the main admin account, but I need it to ask me the new admin account, anyone knows about this?

---

### Post by TheFu on 2023-04-24
> **pbaro said:**
> Hello there!, I have the main admin account, but I had to create 2 new users, one with admin privileges and other with standar privileges. The problem is that the new user with standar privileges if I have to install anything in Ubuntu Software it asks me for the main admin account, but I need it to ask me the new admin account, anyone knows about this?

Regular users cannot install anything.  That's Unix.

You can always open a terminal, use **su - {new-user}**, then run any APT front-end to install stuff.  That's also Unix.

As for which user is the prompt for the GUI stuff, IDK.  I suspect it is either ordered by uid (number) or alphabetical based on the username.

For anyone to help, they probably need to know the exact Ubuntu release, exact DE, and some concrete examples of the 3 usernames involved. Use the 'id' command to get information on each user that can be shared.

Of course, I could be misunderstanding everything.

---

### Post by #&amp;thj^% on 2023-04-24
> **TheFu said:**
> Regular users cannot install anything.  That's Unix.
For anyone to help, they probably need to know the exact Ubuntu release, exact DE, and some concrete examples of the 3 usernames involved. Use the 'id' command to get information on each user that can be shared.

Of course, I could be misunderstanding everything.
+1 Those Details matter...

---

