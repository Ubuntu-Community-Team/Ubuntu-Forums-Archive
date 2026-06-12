---
title: "Hardy Updates...."
date: 2008-06-04
forum: General Help
---

### Post by DeVonne on 2008-06-04
Well, I am too scared to click install updates, I am using hardy ubuntu and I had to reinstall twice due to the computer locking up during updates and crippling it, has anyone else had this?

I finally got it working decently again and do not want to touch the update again..
Should just stay outdated

Your experiences?

---

### Post by kpkeerthi on 2008-06-04
I usually update from command line. You may want to try that. 
```
sudo aptitude update && sudo aptitude dist-upgrade
```

---

### Post by housam on 2008-06-04
updating your system is important. Do not install all the updates at the same time. try to install them in a small groupes .

---

### Post by The Pinny Parlour on 2008-06-04
Yep, I get nervous too.  The amount of times my system rendered completely useless thanks to borked updates.  3-4 and counting.

Anything with Linux image/headers/generic, or nvidia-glx, or Xorg just scares the heck out of me.  I just choose to ignore them.

---

### Post by Sef on 2008-06-04
> sudo aptitude update && sudo aptitude dist-upgrade

You only need to do sudo aptitude upgrade:

```
sudo aptitude update && sudo aptitude upgrade
```

> Anything with Linux image/headers/generic, or nvidia-glx, or Xorg just scares the heck out of me. I just choose to ignore them.

I do get nervous about upgrading too, but so far with my new computer, all has been fine.

---

