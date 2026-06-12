---
title: "installing package problem"
date: 2007-09-30
forum: General Help
---

### Post by elidoperezmd on 2007-09-30
hi all
im trying to instal virtual box
and this  is what happens

elido@elidoperezmd:~$ sudo apt-get install virtualbox
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.

what does this mean? what shloud i do?

thanks for all the help

---

### Post by por100pre1 on 2007-09-30
Maybe a broken package, do as indicated:

```
sudo dpkg --configure -a
```

---

### Post by elidoperezmd on 2007-10-01
tries already...nothing happend. any ideas?

---

### Post by forestpixie on 2007-10-01
well i ended up getting dizzy with that one :)

in the end this worked courtesy of bapoumba

```
sudo dpkg --remove --force-remove-reinstreq virtualbox
```

that should do it for you

---

### Post by geekygreen on 2007-10-01
I was having the same issues...and your code seems to have fixed it.

Thanks...

Is there a forum or thread that specifically addresses Virtual Box?

Note to Self: uncover Note to self to BACKUP system before changing things.  Re-write in LARGE RED LETTERS!  Post on Forehead....](*,)](*,)](*,):mrgreen:

---

### Post by forestpixie on 2007-10-01
not sure if there is a specific forum or thread - but glad it helped you

I got completely fed up sitcking notes on my forehead I started using the kids - works fine till they're at school :D

---

### Post by elidoperezmd on 2007-10-01
i did your sudo dpkg --remove --force-remove-reinstreq virtualbox and now what do i do next?

---

