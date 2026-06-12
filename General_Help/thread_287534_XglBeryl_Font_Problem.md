---
title: "Xgl/Beryl Font Problem"
date: 2006-10-28
forum: General Help
---

### Post by sr243 on 2006-10-28
I just installed Xgl/Beryl according to the directions at
[http://wiki.beryl-project.org/index.php/Install/Ubuntu/Dapper/XGL](http://wiki.beryl-project.org/index.php/Install/Ubuntu/Dapper/XGL)

For the most part, it works fine, but a major problem is that I have really small fonts.

When I logout and use a regular KDE session, the fonts are normal again.

My setup: Xgl/Beryl/ATI card with fglrx/Kubuntu Dapper

Any hints?  Thanks.

---

### Post by sr243 on 2006-10-28
Bump

---

### Post by metanurb on 2006-11-02
Bump
almost same setup (eft) and same problem here :/

---

### Post by metanurb on 2006-11-02
Solved! :p 

found the solution here:
[http://forum.beryl-project.org/post-45201](http://forum.beryl-project.org/post-45201)

> 
Btw there's a better solution... You only have to add to your XGL loading line this option:
```
-dpi XX
```

Where "XX" shows your resolution in dots per inch.


Thomas

---

### Post by Lesterchakyn on 2006-11-16
I recently found out how to fix this problem, using both gnome and kde.

In your Xgl startup script, the -dpi XX can help, but the session start is the troublemaker.

We should change the "exec gnome-session" or the "exec startkde" lines for the following:

exec /etc/X11/Xsession

It will take care of the default fonts and mouse cursors.

Found it out this morning.

---

