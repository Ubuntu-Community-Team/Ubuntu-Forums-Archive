---
title: "&quot;Save&quot; option in terminal"
date: 2015-10-06
forum: General Help
---

### Post by hezy2 on 2015-10-06
Hello,
I've edited a file through terminal but cannot save it before closing the term.. thanks,
hezy.

---

### Post by howefield on 2015-10-06
Which editor did you use to edit the file ?

---

### Post by hezy2 on 2015-10-06
VIM. (command: sudo vim /etc/bacula/bacula-dir.conf)

---

### Post by howefield on 2015-10-06
Press esc key if you are in insert mode, then

```
:w
```  and enter to save the file.

or 

```
:x
``` to save and exit.

---

### Post by coldraven on 2015-10-06
In future you could try using the nano editor, it has the Save etc. commands at the bottom of the window. You don't need an all powerful tool to just edit a config file :)
```
sudo nano /etc/bacula/bacula-dir.conf
```

---

### Post by hezy2 on 2015-10-06
Done :)
thank you.

---

### Post by howefield on 2015-10-06
Welcome :)

---

