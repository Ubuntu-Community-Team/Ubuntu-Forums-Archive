---
title: "How to delete files with root permissions?"
date: 2004-12-05
forum: General Help
---

### Post by pavkonti on 2004-12-05
[http://pavkonti.atspace.com/linux/](http://pavkonti.atspace.com/linux/)

how  can I delete these folders with root permissions and how can I login as root?

---

### Post by HungSquirrel on 2004-12-05
Ubuntu uses a sudo system as explained in [the FAQ](http://www.ubuntulinux.org/support/documentation/faq/root).

To answer your question, to remove a file as root, do *sudo rm filename*.  To browse files as root, do *sudo nautilus*.  (If you do that a lot, you might want to create a launcher whose command is *gksudo nautilus*.)  To login as root, do *sudo -s*.  To enable true root logins, do *sudo passwd root*.  Then you will be able to su as normal.

It took me a while to get used to the sudo model, but now I love it.

---

### Post by wiseNoob on 2004-12-05
If you are looking to remove the folder and it contains files, you would need to do this:
sudo rm -R <folder> (don't include the"<>"...)

the -R is for recursive.  it lets you include the removal of contents, otherwise it will return an error.

---

### Post by pavkonti on 2004-12-05
thank you

---

