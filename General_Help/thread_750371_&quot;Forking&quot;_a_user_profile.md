---
title: "&quot;Forking&quot; a user profile"
date: 2008-04-09
forum: General Help
---

### Post by jim0203 on 2008-04-09
Is there any way of making a complete copy of a user profile - i.e., creating a new user profile which has the same desktop icons, wallpaper, files, permissions etc etc etc?

---

### Post by danwood76 on 2008-04-09
Copy the user home directory, all your settings are contained within this directory.
Some settings may not transfer though if they have absolute paths but most should use relative paths.

---

### Post by SPr on 2008-04-09
As danwood76 said but you may find that you'll have to change the ownership for all the files to the new user to read/write to them.
```

sudo chown -hR USER /home/USER

```
*should* work though I'm not sure whether the "h" switch is needed. Perhaps someone else could give a better way to change ownership.

---

### Post by bodhi.zazen on 2008-04-09
Make a new user and copy the config, or . files to the new user, then chown -R new_user.new_user

where new_user = new user name.

---

