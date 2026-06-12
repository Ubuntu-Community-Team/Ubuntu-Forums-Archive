---
title: "Users &amp; groups"
date: 2008-06-27
forum: General Help
---

### Post by Pabx on 2008-06-27
Hi, can i make another user from terminal using root account? how?

---

### Post by tamoneya on 2008-06-27
```
sudo useradd joe
sudo passwd joe
```

---

### Post by Pabx on 2008-06-27
OK this is what happened :

your home directory is listed as /home/user/ but it does not appear to exist do you want to log in with the root directory as your home directory? it is unlikely anything will work unless you use a failsafe session.

what can i do?:confused:

---

### Post by tamoneya on 2008-06-27
```
sudo mkdir /home/user
sudo chown user /home/user
sudo chgrp user /home/user
```

---

