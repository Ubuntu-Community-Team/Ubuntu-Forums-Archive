---
title: "Changed user id - Now get login loop"
date: 2013-11-13
forum: General Help
---

### Post by the_dingman on 2013-11-13
Greetings!

I changed a user id to 499 to make it a hidden user, and now I get a login loop when I attempt to log in.  If I log in via shell, I get in, but get an error "fopen: permission denied" above my command prompt.  This is an encrypted-home user.  Any ideas?

---

### Post by the_dingman on 2013-11-14
Is there anyone with experience with this problem?  I am finding no luck on google, and have reinstalled twice to see the same problem, only after changing the user ID.

---

### Post by efflandt on 2013-11-15
Did you remember to recursively chown that user's entire home directory to that new user:user after changing the user ID?

But why do you think that changing your user ID would make you a hidden user? Why not just remove x and r permission from your home directory for others so nobody else can access it?

---

### Post by Habitual on 2013-11-15
> **the_dingman said:**
> Any ideas? Change it back?

---

