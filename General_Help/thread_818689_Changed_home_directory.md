---
title: "Changed home directory"
date: 2008-06-04
forum: General Help
---

### Post by Linuxxx on 2008-06-04
Hello.. i just made a big mistake in Ubuntu and changed my home directory to /root

now it won't let me in since it don't have permission to write in root

Now, is there a way to change back to my old home directory using ctrl+alt+F1?

---

### Post by sdennie on 2008-06-04
Probably, yes.  If you Ctrl-Alt-F1 and then login, it should let you in.  After that you should be able to:

```

sudo usermod -d /home/your_username your_username

```

If you can't login at all, you can also start in recovery mode to do this.

---

### Post by Linuxxx on 2008-06-04
*Solved

For ppl with similar problem the solution:

sudo nano /etc/passwd

Locate the user and change /root to /home/whatever it was

---

