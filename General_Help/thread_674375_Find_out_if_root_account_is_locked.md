---
title: "Find out if root account is locked"
date: 2008-01-21
forum: General Help
---

### Post by makmiler on 2008-01-21
Hi,

how can I find out if the root account is locked or not?

its better if someone can tell how this can be done in terminal, and not using some gui program.

Best regards,
makmiler

---

### Post by Het Irv on 2008-01-21
If you type a sudo command and it asks for your password, root is locked.  If it does not prompt you for your password it is unlocked.  The sudo part of the command is read first so commands that don't exsist will still ask for your password.  If you don't want to unlock root just close the terminal.

---

### Post by aysiu on 2008-01-21
Type ```
sudo nano /etc/shadow
``` At the top, there should be a line for root. If a colon and exclamation mark appear right afterwards, then root is locked. ```
root:**!**:13896:0:99999:7:::
```

---

### Post by makmiler on 2008-01-21
Thank you for the fast answer. That is what I was looking for. ;)

---

