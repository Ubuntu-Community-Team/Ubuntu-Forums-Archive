---
title: "How do you use sudo in a script or app launcher?"
date: 2007-03-07
forum: General Help
---

### Post by Carl H on 2007-03-07
I have several PCs and have NFS set up so I can share some folders between them. As I don't always have each PC powered up, I haven't had these shares mapped at boot time. Instead, I just mount them from the command line when I need them. 

I have since added a launcher to the top Gnome panel to do this, but it prompts me for the password each time. The command that the launcher runs is

```
sudo mount 192.168.0.4:/stuff /mnt
```

Is it possible to include the password in this command so that it just does it when I run the launcher, instead of asking for the password? 

I know this isn't great practice, but there's only me and the wife who have access to these PCs, and the wife doesn't know how to switch them on, let alone get up to mischief with the root password. :)

---

### Post by nereid on 2007-03-07
You could use gksudo instead of the command line sudo. gksudo will display a nice GTK window asking for your password.

On the other hand you could disable your sudo password. But it ain't possible to provide sudo (or its derivates) with a password in the command line.

---

### Post by Carl H on 2007-03-11
Thanks for that. gksudo is something of an improvement.

---

