---
title: "Pasting text in JAva app, garbage characters -- Not found: text/html"
date: 2015-10-27
forum: General Help
---

### Post by jmkowske on 2015-10-27
I am posting this here because the application support has told me they cannot reproduce it. I'm hoping this forum has some insight.

I am running software called TheBrain ([http://thebrain.com/](http://thebrain.com/)) that is a Java app on Ubuntu 15.04.  My current Java version is Oracle Java 8 Update 66.

The problem is when I paste into this application anything that is not  plain text I get a bunch of garbage characters (along with the plain text). It looks like the attached pic:

[IMG]http://i60.tinypic.com/2my7t49.png[/IMG]

When I paste it is accompanied by a warning message in the application log:

```
208104 [AWT-EventQueue-0] WARN com.thebrain.personal.h.u - Not found: text/html
```

To me this looks like something is having trouble finding a MIME type, but I don't know. I have tried multiple different versions of Java and multiple installs of Ubuntu. I have never found a scenario where I didn't have this issue yet TheBrain support staff says they cannot reproduce the problem on Ubuntu. I have tested other Java apps and pasting works fine. Running out of ideas .... thoughts?

edit: I just confirmed this only happens when I copy from Firefox. Chrome does not experience the issue.

---

### Post by col48 on 2015-10-27
No idea what's going on, but you may get an idea by pasting what you hope is the same thing from Firefox & Chrome into gedit or LibreOffice Writer and seeing what is different.

---

