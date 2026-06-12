---
title: "Web dev server won't read &quot;images&quot; dir (Apache)"
date: 2007-01-05
forum: General Help
---

### Post by chocolatetoothpaste on 2007-01-05
Hey all,
I am having a real screw ball of a problem.  I am running a web development server, and anytime I have a folder in the document root named "images", for some reason apache/my web page can't read anything inside this dir.  If I rename it to images2 or anything else, it works fine.  Can someone help with this terribly annoying problem?  I have it on 2 machines and it is pissing me off!

---

### Post by chocolatetoothpaste on 2007-01-05
Nevermind, everyone.  I figured it out.  There was an alias defined in the httpd.conf file.  I just commented that out, and it works fine.  Thanks to all those who would have helped!

---

