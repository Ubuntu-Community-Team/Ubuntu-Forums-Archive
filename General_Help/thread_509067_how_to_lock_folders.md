---
title: "how to lock folders"
date: 2007-07-25
forum: General Help
---

### Post by Error47 on 2007-07-25
How do I lock a folder so that I have to put a password to view it's contents?
and also, to hide a folder to. Like so i would have to click on view hidden folders to see it, like the windows function

---

### Post by simonn on 2007-07-25
Hiding is done by placing a full stop/period before the name e.g.:

```

.hidden-folder

```

You cannot "lock a folder so that I have to put a password to view it's contents?", unless you look at using an encrypted file system. However, what you can do is:

1) create a group called, for example, "hidden" (without the quotes)

```

$ sudo groupadd hidden

```

2) Make the folder owned by root:hidden

```

$ sudo chown root:hidden [folder]

```

3) Change the permissions on the folder so that only members of the group "hidden" have access

For read only access:

```

$ sudo chmod 750 [folder]

```


For read write access:

```

$ sudo chmod 770 [folder]

```

Only users who are members of the group "hidden" will have access to the directory. How you make users a member of the group you can work out yourself using rutes guide in my sig.

EDIT: Doh!

---

### Post by yopnono on 2007-07-25
Try this:
[http://ubuntuforums.org/showthread.php?t=504371](http://ubuntuforums.org/showthread.php?t=504371)

---

