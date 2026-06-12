---
title: "[SOLVED] Firefox 3 refuses to use Java"
date: 2007-12-19
forum: General Help
---

### Post by Ub1476 on 2007-12-19
I've been working around trying to get Java to work on Firefox beta 3, ands it just wont work. I've made a symbolic link in both /home/user/.mozilla/firefox3/plugins and usr/lib/firefox/pllugins. I've also tried to "pluginreg.dat" file without any succes. In "about:plugins", only Macromedia Flash is listed. Java works fine in Firefox2/Epiphany/Swiftfox2. It does not work in Swiftfox 3 though.. 

So what's wrong with Firefox 3?

---

### Post by Ub1476 on 2007-12-20
bump

---

### Post by Ub1476 on 2007-12-21
I figured it out myself. It was because the plugin was owned by root, which didn't gave read and write permissions to "groiup/user, in other words: Firefox.

---

### Post by avelez89 on 2008-03-28
Could you explain how to solve it for us noobs out there please?

---

### Post by tubasoldier on 2008-03-28
I had the same issue but I just copied the Java plugin into my .firefox3 directory. It worked a lot easier than changing permissions.

The Java plugin file is in /usr/lib/mozilla/plugins or possibly in /usr/lib/firefox/plugins I believe? someone correct me if i'm wrong.
Just copy it and paste it into your ~/.firefox/plugins directory

---

