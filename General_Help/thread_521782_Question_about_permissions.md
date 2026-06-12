---
title: "Question about permissions"
date: 2007-08-09
forum: General Help
---

### Post by bggashnik on 2007-08-09
How can I get full access to the system(to be able to edit and delete all files I want to and execute commands without typing any password or using sudo command?

---

### Post by mike102282 on 2007-08-09
Give yourself root access

---

### Post by merlinus on 2007-08-09
And be sure to triple-check rm commands (e.g. rm -R /).

:mrgreen:

-merlin

---

### Post by bggashnik on 2007-08-10
And how to give myself root access?

---

### Post by mcduck on 2007-08-10
in terminal, use "sudo -i" to open a root session. On desktop, run "gksudo nautilus" to open file manager as root.

---

### Post by bggashnik on 2007-08-10
But how to make my username with all rights?The same permissions as root?

---

### Post by mrmonday on 2007-08-10
You may as well just log in as root. I'll point out that it is a serious security risk running as root, and isn't recommended.To log in as root, you must first enable it, by going to System > Administration > Login Window, then going to the security tab, and checking 'Allow local system administrator login'. You will then be able to log in as root. Spend as little time as possible logged in as root, and disable logging in as root once you are done.

---

### Post by l5nrr on 2007-08-10
with respect, if you have to ask a question about such a simple thing, you don't want to be running as root. Very easy to do lots of damage.

---

### Post by bggashnik on 2007-08-10
I'm not new to linux i'm just new to ubuntu.That's why a'm asking

---

