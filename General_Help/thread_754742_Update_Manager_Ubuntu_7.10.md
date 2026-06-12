---
title: "Update Manager Ubuntu 7.10"
date: 2008-04-14
forum: General Help
---

### Post by Mojo99 on 2008-04-14
While downloading two small updates 3 days ago my system crashed.

Since then when I start Update manager manually it hangs while building dependency list.
I also cannot install any other new software I have downloaded (Skype) The install hangs in the same way Update Manager does.

I am also not receiving notification of daily updates.

How do I fix the problem with Update Manager?

---

### Post by PmDematagoda on 2008-04-14
Can you post the exact error when you do:-
```
sudo apt-get install -f
```
and
```
sudo dpkg --configure -a
```

---

### Post by Mojo99 on 2008-04-14
sudo apt-get install -f

This gives;

Reading package list... done

Building Dependency tree...50%

After several minutes it is still sitting with a blinking cursor and has gone no further.

sudo dpkg --configure -a

This gives nothing. It just goes to a new command line and waits for a new command

No error messages unfortunately.

Hope this is useful to track down the problem.

---

