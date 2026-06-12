---
title: "Question regarding gnome-session.1.gz"
date: 2007-01-09
forum: General Help
---

### Post by Interestedinthepenguin on 2007-01-09
Hello.

I'm going to install the package, gnome-session_2.14.3-0ubuntu2_i386.deb, but I want to backup my current version of gnome-session (2.14.1-0ubuntu11).  

I ran ```
whereis gnome-session
``` in the terminal, and the output was:

```
gnome-session: /usr/bin/gnome-session /usr/bin/X11/gnome-session /usr/share/man/man1/gnome-session.1.gz
```

Seeing as there is a gnome-session.1.gz, I was wondering:  Can I just backup the .1.gz file, instead of backing the other directories up, and unpack gnome-session.1.gz (having it install to the directories listed above?:-k 

Thanks.

---

### Post by taurus on 2007-01-09
/usr/share/man/man1/gnome-session.1.gz is just a manpage so no need to back that up!  The one you want to back up is /usr/bin/gnome-session.

---

### Post by Interestedinthepenguin on 2007-01-09
> **taurus said:**
>  The one you want to back up is /usr/bin/gnome-session.

Okay, thanks. :) 

I hope you don't mind me asking...but what about /usr/bin/X11/gnome-session?  

What is that?

---

### Post by taurus on 2007-01-09
I am sure that one, /usr/bin/X11/gnome-session, is pointing to /usr/bin/gnome-session.  If not, back that up too.  ;)

---

### Post by Interestedinthepenguin on 2007-01-09
Alright.  

Thanks again. :)

---

### Post by taurus on 2007-01-09
You're welcome.

---

