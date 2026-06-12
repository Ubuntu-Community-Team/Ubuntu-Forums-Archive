---
title: "change to sudo on demand"
date: 2007-03-26
forum: General Help
---

### Post by josephus on 2007-03-26
I am wondering if there is a way to change a program that was started as a regular user to one that the system will believe that was started using the sudo command.

For instance, sometimes I edit the xorg.conf with gedit xorg.conf when I really should have started the program as 'sudo gedit xorg.conf'.  After I've made changes and I want to save the file the system won't let me because it's a read only file for the regular user, and it's annoying to start over again.  Is there a way around this by changing who is running a programming from the command line?

Thanks.

---

### Post by aysiu on 2007-03-26
This isn't *exactly* what you're looking for, but you could always save the file to your home directory and then move it over later to /etc/X11

I think your best bet, if you're making a lot of system changes, is to make a keyboard shortcut and/or panel icon for the command ```
gksudo nautilus
```

---

### Post by zvacet on 2007-03-27
Download nautilus script with Automatix or install it by yourself
[http://doc.gwos.org/index.php/Nautilus_Scripts]("http://doc.gwos.org/index.php/Nautilus_Scripts")

---

### Post by josephus on 2007-03-28
Not quite what I was looking for, but thanks for the suggestions.

---

