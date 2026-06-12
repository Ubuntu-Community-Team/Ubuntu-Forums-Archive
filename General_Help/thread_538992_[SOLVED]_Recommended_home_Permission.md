---
title: "[SOLVED] Recommended home Permission?"
date: 2007-08-30
forum: General Help
---

### Post by L8erG8er on 2007-08-30
Sorry if this is a repeat question.  What is the recommended permission level for the /home directory?
Thanks everyone.

---

### Post by merlinus on 2007-08-30
This is for /home/user.

owner=user - read/write (create and delete files}
group=user - read only (access files}
others - read only (access files}

-merlin

---

### Post by L8erG8er on 2007-08-30
Thanks, Merlin.  I recently had a little ".dmrc" episode, and even though everything is now working, I think I've allowed too much access.  Thanks again.

---

### Post by merlinus on 2007-08-30
I had the same thing happen, which is how I learned.

-merlin

---

### Post by bmorency on 2007-08-30
you can also set it so only the owner can read their own folder using:

```
sudo dpkg-reconfigure adduser
```

---

### Post by L8erG8er on 2007-08-31
> **bmorency said:**
> you can also set it so only the owner can read their own folder using:

```
sudo dpkg-reconfigure adduser
```

Thanks, bmorency, but I'm not sure I understand what this will do.

---

### Post by bmorency on 2007-08-31
> **L8erG8er said:**
> Thanks, bmorency, but I'm not sure I understand what this will do.

if you run that command a config screen will show up and ask you if you want each user's home folders readable by everyone or just the user it belongs too. so the permissions on /home/nameofuser will be:

owner = rwx
group = ---
other = ---

instead of what merlinus said. so the user "nameofuser" will only be able to read his folder and not others under the /home folder.

---

### Post by L8erG8er on 2007-08-31
Cool.  I see what you mean.  Thanks, bmorency.

---

