---
title: "X dies first time it is astarted on bootup and password has to be entered twice."
date: 2006-11-17
forum: General Help
---

### Post by slavik on 2006-11-17
This is in Dapper (although the second problem happens in Edgy, too).

1. Basically, when I try to login through GMD or through the virtual console, I enter my username and password (correctly), then I get asked for my password again. This also prevents gksudo from working properly.

2. When I log in through GDM (or have it automatically log me in), X dies and then is restarted by GDM with a login window. After logging in through GDM a second time, X does not die.

3. Automounting stopped working

---

### Post by slavik on 2006-11-17
sorry, double post.

---

### Post by taurus on 2006-11-17
Try to change your password to something new and reboot.  See if it still happens with the new password!

```
passwd
```

---

### Post by slavik on 2006-11-17
well, that fixed the double password thing and the X dying ...

USB automounting still doesn't work.

---

### Post by slavik on 2006-11-28
well, I had my computer join active directory and the problem re-appeared ... changing the password, does not help ... any ideas?

---

