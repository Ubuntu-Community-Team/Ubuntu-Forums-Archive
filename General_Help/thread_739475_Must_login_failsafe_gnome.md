---
title: "Must login failsafe gnome"
date: 2008-03-29
forum: General Help
---

### Post by protenniser on 2008-03-29
Hi all,

While messing with my graphics and screen settings, I think I also messed up another thing so that I can not open the computer (session) as normal mode but only in failsafe mode.
When I try normal login, there appears an error message that starts like this.
```

Your session only laster less than 10 seconds........ (some other things) and at the end it says that there is an error message in ~/.xsession-errors

```
When I try to look for error it is like this:
```


(process:5359): Gtk-WARNING **: This process is currently running setuid or setgid.
This is not a supported use of GTK+. You must create a helper
program instead. For further details, see:

    http://www.gtk.org/setuid.html

Refusing to initialize GTK+.

(process:5372): Gtk-WARNING **: This process is currently running setuid or setgid.
This is not a supported use of GTK+. You must create a helper
program instead. For further details, see:

    http://www.gtk.org/setuid.html

Refusing to initialize GTK+.
/etc/gdm/Xsession: Beginning session setup...
/etc/X11/Xsession.d/39keytouch-acpid: 2: Syntax error: "&" unexpected

```
I have uninstalled keytouch but I am still getting the same error. I can login in failsafe mode without any problems.

1st question: What is the disadvantage of failsafe mode?
2nd question: How can I fix this? :)
Thanks in advance...

---

### Post by tad1073 on 2008-03-29
did you move or rename your /home folder?

---

### Post by protenniser on 2008-03-29
No it is where it supposed to be :D
Or at least I can see it as /home from the file system.

---

### Post by protenniser on 2008-03-30
Gurus, please help!
This started to bore me a lot. Please help!...
I want to recover my old gnome!
Thanks in advance.

Edit: The problem has resolved after I removed that two files in the error message!

---

