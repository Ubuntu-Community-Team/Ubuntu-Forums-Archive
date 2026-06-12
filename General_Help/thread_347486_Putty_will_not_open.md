---
title: "Putty will not open"
date: 2007-01-27
forum: General Help
---

### Post by SVFUSiON on 2007-01-27
I did a apt-get install putty and now when I try to run it i get this error,

Gtk-WARNING **: cannot open display:,

any ideas?

Thanks!

---

### Post by Shortgeek on 2007-01-27
I don't know what's happening, but I do know I get a similar error trying to start a graphical app from the Ctrl-Alt-Fn terminals. (Terminal emulators on X start them fine.) I don't know what this means, but it's the same error message. Are you trying to start putty from the command line, and is putty a graphical app?

---

### Post by Tomosaur on 2007-01-27
If X isn't running, you won't be able to start graphical apps. A command line ssh client is called, simply enough, 'ssh'.

---

### Post by SVFUSiON on 2007-01-27
X is running,  the command SSH doesn't allot be login to other accounts.

---

### Post by SVFUSiON on 2007-01-27
I got it working. All I needed to do is make a launcher.

Thanks!

---

### Post by JamieC on 2007-01-27
> **SVFUSiON said:**
> X is running,  the command SSH doesn't allot be login to other accounts.

Explain? You can login using any user with the -l switch (login_name):
```

ssl <host> -l<user>

```

---

