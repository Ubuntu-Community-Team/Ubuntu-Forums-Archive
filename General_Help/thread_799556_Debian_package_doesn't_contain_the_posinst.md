---
title: "Debian package doesn't contain the posinst?"
date: 2008-05-19
forum: General Help
---

### Post by nahed on 2008-05-19
hi everybody,
i'm creating a debian package and when i generate a package.deb it normally contains a control.tar.gz with the following files:
posinst
preinst
control
md5sums

But in my case it only adds the control and md5sums files. How can i force adding posinst into the control.tar.gz? is there a particular command that i should add in my debian/rules?

---

### Post by ibuclaw on 2008-05-19
Files must be named "**preinst**" and "**postinst**".

Also, your scripts must start with a "**#!/path/shell**" style header.

They must also be compliant with the Debian standards, you can't just go off and write any sort of script you want to run.

Read [here.]("http://www.debian.org/doc/debian-policy/ch-maintainerscripts.html")

Regards
Iain

---

### Post by nahed on 2008-05-20
thank you for your help. it worked very well. the problem was in the postinst. By default i use the debuild command which generates a postinst.ex. so i renamed postinst and give it executable right.

---

