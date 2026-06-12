---
title: "Editing username"
date: 2007-01-02
forum: General Help
---

### Post by Bider on 2007-01-02
Is it possible to edit the username of the main admin account, without having to create a new user Instead of > "blah@blah-desktop:$" with "newblah@newblah-desktop:$" in terminal or otherwise.

---

### Post by radu_chindris on 2007-01-02
```

sudo usermod -l new_uname uname

```

---

### Post by Bider on 2007-01-02
Thanks, what about after the username such as @blah-directory. is that changable as well?

---

### Post by ikonia on 2007-01-02
the @ bit is the hostname after it

@hostname really.

you may have problems using usermod if the username you're trying to alter is in use.

---

