---
title: "Svn help!"
date: 2007-03-02
forum: General Help
---

### Post by olskar on 2007-03-02
Hi!
I made a directory with svn mkdir /url/newdir

Then I checkedout that new directory and created a textfile in there.

The I typed  svn commit mjaha.txt to upload it

And I get:

svn: '/home/askar/askars/mjaha.txt' is not under version control

How do I upload it?

---

### Post by ziggykg on 2007-03-03
You have to add the file first using 'svn add' command before you can commit it into SVN.

---

