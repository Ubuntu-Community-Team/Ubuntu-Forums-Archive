---
title: "How to delete oldest folder"
date: 2018-08-11
forum: General Help
---

### Post by Old Jimma on 2018-08-11
Hi Community:

I need to write a shell script that deletes the oldest directory in a specified directory.

(I'll add the script to a crontab job to help back up recent and delete old folders.)

There is is guidance on how to do this at stackechange: [https://unix.stackexchange.com/questions/28939/how-to-delete-the-oldest-directory-in-a-given-directory]("https://unix.stackexchange.com/questions/28939/how-to-delete-the-oldest-directory-in-a-given-directory")

However, there doesn't seem to be anything in that advice that works.

Can somebody help me out with this?

Thanks,
Old Jimma

---

### Post by Old Jimma on 2018-08-11
HI All:

I found a script that works:

** rm -R $(ls -t1 | tail -n 1)**

However, this script requires that there is NO WHITESPACE in the directory names!

OJ

---

### Post by edadasiewicz on 2018-08-12
Just add some double quotes:

rm -R "$(ls -t1 | tail -n 1)"

---

### Post by Old Jimma on 2018-08-15
thanks, edadaslewicz

---

