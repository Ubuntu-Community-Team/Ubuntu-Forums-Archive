---
title: "Why doesn't locate find files that exist in my filesystem??"
date: 2008-01-29
forum: General Help
---

### Post by theodorekon on 2008-01-29
The problem is that sometimes locate does not find some files that I know they are in my Filesystem. Nor can I find them with "Search for files..." in the Places menu. It finds nothing  although I can find them manually. I didn't have that kind of problem with fedora. Is there a way to fix that??

---

### Post by bodhi.zazen on 2008-01-29
Can you post an example ? If the files are new you need to update the data base (normally done daily via cron)

sudo updatedb

---

### Post by amo-ej1 on 2008-01-29
Or you could learn to work with find, which actually scans the disks instead of rely on a database (like updatedb does).

---

### Post by theodorekon on 2008-01-30
I guess the problem was that my files were recently added to the computer. I tried slocate -u and then I used locate and it worked. Thanks anyway!! :)

---

