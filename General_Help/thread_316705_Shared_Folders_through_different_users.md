---
title: "Shared Folders through different users"
date: 2006-12-11
forum: General Help
---

### Post by hoagie on 2006-12-11
Hello there ubuntu comunity,
On this computer there are 2 users. Me and my sister's one(and root of course)

My problem is that we want to share some folders between the two users. Is this possible ? If yes how?

Edit: After looking around I found that going through /home/username/* you can bsowse all the users folders, so is this the right way to do it?

---

### Post by taurus on 2006-12-11
If you want your sister to write to your own $HOME directory, then you need to set the permissions so that she can do that...

```
chmod -R 777 /home/**your_username**
```
Otherwise, create a /share directory and use that to share files with different users instead.  It's more secure that way in case she messes up your settings in your $HOME directory.

---

### Post by hoagie on 2006-12-11
Ok thanks alot

---

