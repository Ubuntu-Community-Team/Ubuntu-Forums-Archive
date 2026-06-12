---
title: "used space in HD partition"
date: 2006-07-10
forum: General Help
---

### Post by macozz on 2006-07-10
Hi,
I was checking the available space in my HD and discovered that the /home partition (which is 12.57 GiB in size) has only 5.65 GiB free, which mean 7.22 GiB are used. However, when the actual ocuped space is cheked (by looking at the total files size of the /home partition, including the hiden files and directories) it show that only 3.3GiB are used.
So, what is using/locking the remaining 3.92GiB that is suposed to ocuped?
All the other partionn (/ , /usr, /boot) are OK and show the actually occuped   space.
I used some times the hibernation, so is it possible that this ocuped the space without freeing it later?
Any ideas are welcomed!

---

### Post by Paerez on 2006-07-10
hello

if you run:
```
# du -sh ~
```
in a terminal, it will tell you how much each folder takes up.

You can change the ~ to a folder name to see the folders inside that folder. If you remove the s parameter (so its "du -h ~") you can see every folder. If there is too much information to scroll, do this:
```
# du -h ~ | less
```
then use the arrow keys and page up/down to view the output.

It gives you a very detailed view of where all your space goes.

---

### Post by macozz on 2006-07-10
Thanks!
It helps indeed.
I found a hiden folder under ~.local/share/ called Trash, with 1.5GiB... and I cannot realize how it became this size! It is certanly not linked t the Gnome or KDE trash....
Thanks again!

---

### Post by Paerez on 2006-07-10
another handy command may be:
```
# find ~ -name '[Tt]rash'
```
This will find any folders named "Trash" or "trash" in your home dir.

Yeah those pesky hidden folders are trouble :D

---

### Post by mduran on 2006-07-10
and other command

```

find ~  -maxdepth 1 -exec du -s {} \; |sort -n |less

```

order 1 level of directory, min to max (for page)

---

