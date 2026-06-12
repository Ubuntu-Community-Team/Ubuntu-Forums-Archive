---
title: "Login troubles"
date: 2007-02-13
forum: General Help
---

### Post by superman736 on 2007-02-13
My username and are both right but every time I try to login the screen goes black for a split second and it returns me to the login screen. Can anybody please help?

---

### Post by bapoumba on 2007-02-13
First try to log in a tty by CTRL-ALT-F2, and run **df -h**.
Check if you root (/) or /home (if separate) partition are full, and make some room.

If you cannot log into tty, reboot in recovery mode from grub. Careful, you'll be root ;)

---

### Post by superman736 on 2007-02-13
Yeah I have no memory left, so how do I delete some files without logging in?

---

### Post by taurus on 2007-02-13
Boot into recovery mode from GRUB menu and at the prompt, do

```
sudo aptitude clean
rm ~/.Trash/*
rm /home/**username**/.Trash/*
df -h
```
Replace the **username** with the actual name that you log in with.

---

### Post by superman736 on 2007-02-13
Thank you bapoumba and taurus  you guys saved me from reinstalling thanks very much.

---

### Post by bapoumba on 2007-02-13
You're welcome :)
Reinstalling is rarely needed ;)

---

### Post by Jason Weiss on 2007-02-17
i am having the same problem. 

but when I try to follow your instructions it give me a message which says "no such file or folder as "*" found"

what am I doing wrong 

Is there another way I can acheive the same outcome?

---

### Post by bapoumba on 2007-02-17
Hi,
Did you run the **sudo aptitude clean** ? This should free some room on your root (/) partition.

**ls ~/.Trash/*** will show you if your user Trash file is empty or not. Delete what's in it with Taurus's command.

To browse your current directory for top 10 big files:
```
du -ha |sort -n -r |head -n 10

```

---

