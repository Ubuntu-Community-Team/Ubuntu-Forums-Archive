---
title: "Splitting and Combing files"
date: 2006-11-02
forum: General Help
---

### Post by sefs on 2006-11-02
Hi.  I want to split a file into parts using the split command on ubuntu, and then reassemble those parts on a windows machine.

Is this possible on the windows side? if so, how so.

Thanks.

---

### Post by yabbadabbadont on 2006-11-02
If you have split the file into part1, part2, and part3, then use the copy command like this:

copy /b part1+part2+part3 combinedfile

---

### Post by sefs on 2006-11-02
Thank you my brother!

---

### Post by yabbadabbadont on 2006-11-04
You are welcome.  It's funny the things you learn when using "sneaker-net" to transfer files from a Unix system to DOS.  (on floppies)  ((many, many years ago))

---

