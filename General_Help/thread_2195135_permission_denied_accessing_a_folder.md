---
title: "permission denied accessing a folder"
date: 2013-12-22
forum: General Help
---

### Post by codenine75a on 2013-12-22
I answered my own question and just documenting it here as a resolved issue that someone else may have.
in your terminal type 
```

sudo xterm

```
..and now you are operating with root permissions under a console.
This is because for some strange reason 
```

sudo cd "MY FOLDER"

```
does not work.  cd cannot be elevated
ALSO to fix the issue try this
```

sudo chmod 777 "MY FOLDER"

```
This gives all permissions to every account for read, write, and execute.  (Caution that number is a forbidden number in some countries... I think they are asian countries)

---

### Post by philinux on 2013-12-22
You would never normally need sudo to access any folder in a users home.

---

### Post by oldos2er on 2013-12-22
Bash shell commands like "cd" can't be sudo'ed, as you found out. Aside from ```
sudo xterm
``` you could also use ```
sudo -i

cd /root/foo
``` for example.

---

