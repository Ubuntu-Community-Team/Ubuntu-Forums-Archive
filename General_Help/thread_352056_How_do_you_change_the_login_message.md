---
title: "How do you change the login message?"
date: 2007-02-02
forum: General Help
---

### Post by grte on 2007-02-02
You know how when logging in via a tty, you'll get this message:

```
Linux xxxx 2.6.17-10-generic #2 SMP Tue Dec 5 22:28:26 UTC 2006 i686

The programs included with the Ubuntu system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by
applicable law.
No mail.

```

Does anyone know where to go to change this?  And if so, do you know how I can use the fortune app with it?

---

### Post by kairu0 on 2007-02-02
```
gksudo gedit /etc/motd
```

---

### Post by kpatz on 2007-02-02
Use kairu0's suggestion to edit the motd file to change the message.

To get a fortune to display when you login, add /usr/games/fortunes to your .bashrc file.

---

### Post by scxtt on 2007-02-02
the only way i can think of to use fortune w/ /etc/motd would be to have a cron that does:

fortune > /etc/motd

every so often ... but if you want a different fortune each time you login - not sure about that ... maybe you can edit ~/.profile (or ~/.bash_profile) to do that ...

---

### Post by grte on 2007-02-02
Okay, thanks.  Another question, is it possible to use variables in the motd?  For example, could I use Welcome to <localhost> $USER?

---

### Post by 23meg on 2007-02-02
> **grte said:**
> Okay, thanks.  Another question, is it possible to use variables in the motd?  For example, could I use Welcome to <localhost> $USER.No, it's just displayed as is, not parsed for variables.

---

