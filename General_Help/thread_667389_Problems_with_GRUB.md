---
title: "Problems with GRUB"
date: 2008-01-14
forum: General Help
---

### Post by psychowatermelon on 2008-01-14
ok i must first state that everything installed great however GRUB
has been a pain.


initially i installed 7.10 x64 on my slave drive. however i re installed
7.10 i386 for better driver support. when grub made the menu.lst file
it set my boot menu incorrectly. all three ubuntu load entries state
mounting of (0,0) when it should be (1,0) and and Win XP SP3 shows
as (0,1) and (1,0) when it should be (0,0) and (0,1).

now my question is how can i get GRUB to read this right.

i have edited the file using nano via the sudo nano from console and
the the changes stay until i restart the system. Then it shows the 
previous settings and the damn splash quiet is back as well. The
file i edited was /boot/GRUB/menu.lst as this was the same file i had 
edited before for GRUB on a SUSE 7.1 system years ago.

P.S. yes i know windows is the devil but i still have to
get a linux copy of my cad software :-({|=

---

### Post by x1a4 on 2008-01-14
Welcome to the forum.

Once you've made changes to GRUB execute ```
sudo /sbin/update-grub
```

---

### Post by psychowatermelon on 2008-01-14
ah ok wow i guess its been  a while didn't not even remember that one.

---

### Post by psychowatermelon on 2008-01-14
ok on trying this over lunch ut did what it was supposed to do. however
it just mapped that drives in Grub back to original.  i tried  sudo vi /boot/grub/menu.lst 
and was successful in editing grub. for some reason nano just would not overwrite the
file even when run from root terminal.

nks for the in for tho **x1a4**

---

