---
title: "[SOLVED] Trash corrupted - weird links to system dirrectories"
date: 2007-08-30
forum: General Help
---

### Post by chewearn on 2007-08-30
I have a strange problem with my Trash, see screenshot.
When I click on any of the items, it go to a file or directory inside /var/run
Needless to say, I cannot empty the trash.

$ ls -al ~/.Trash
total 8
drwxr-xr-x  2 user1 user1 4096 2007-08-30 18:42 .
drwxr-xr-x 47 user1 user1 4096 2007-08-30 18:42 ..

$ sudo rm -Rf ~/.Trash/*

did not solve the problem. :(  Any idea, anyone?  Thanks.

---

### Post by jim_p on 2007-08-30
Just a thought for now. Open up a window and press Ctrl + L.
This will get you to the address bar where you type
```
trash:
```

Is this the recycle bin now?
I will look it up an come up with an answer soon

---

### Post by chewearn on 2007-08-30
> **jim_p said:**
> Just a thought for now. Open up a window and press Ctrl + L.
This will get you to the address bar where you type
```
trash:
```Is this the recycle bin now?
I will look it up an come up with an answer soon

Thanks for the suggestion.  I'm away from my notebook right now (where I have this problem); will try it out when I get back.

---

### Post by chewearn on 2007-08-30
Ok, have tried out CTRL+L, then trash:
I see the same /var/run contents in the Trash.

---

### Post by chewearn on 2007-08-30
Ok, after googling "/var/run trash" (doh!:redface: should have done this in the first place), came across this:
[https://bugs.launchpad.net/ubuntu/+bug/120884](https://bugs.launchpad.net/ubuntu/+bug/120884)

Instead of deleting the file .trash_entry_cache (like what the launchpad OP did), I edit it:

Original file:
```
/dev/shm -
/lib/modules/2.6.20-16-generic/volatile -
/proc/bus/usb -
/var/lock -
/var/run /var/run
```Edited to:
```
/dev/shm -
/lib/modules/2.6.20-16-generic/volatile -
/proc/bus/usb -
/var/lock -
/var/run -
```Not sure exactly what the changes did, but it worked.  After logout/login, the trash is back to normal.

---

