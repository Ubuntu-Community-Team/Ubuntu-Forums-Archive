---
title: "tmpfs usage in a home unit"
date: 2014-08-08
forum: General Help
---

### Post by ibjsb4 on 2014-08-08
I have been searching for suggestions on what files to move to tmpfs so far have came up with the following

/tmp
var/cache
var/run
var/lock

What I wonder is this a good idea on a home unit or better left alone since this is not a high traffic machine.  The goal is not necessary performance (speed), but to reduce disk access.

Other than my sql are there any other files that could make use of tmpfs?  Again, this is not so much performance, but to reduce disk access.  

And yes, I do realize some files will need to be backed up to hdd.  My backup strategy is rsync.

I have 24G of ram.

Thanks for reading :)

---

### Post by ibjsb4 on 2014-08-09
bump

---

### Post by Jesse_Campton on 2014-08-09
I am not too familiar in your case, however after doing a little bit a research, I found another thread that may interest you! [http://ubuntuforums.org/showthread.php?t=1413653](http://ubuntuforums.org/showthread.php?t=1413653)

---

### Post by ibjsb4 on 2014-08-09
> however after doing a little bit a research

I did a lot of research and did not hit on this thread.

Your google-fu is good, thanks :)

---

### Post by coffeecat on 2014-08-11
Closed at request of OP.

---

