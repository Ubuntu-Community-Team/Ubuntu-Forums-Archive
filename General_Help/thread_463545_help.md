---
title: "help"
date: 2007-06-03
forum: General Help
---

### Post by thedarkside123 on 2007-06-03
i installed wubi
it worked several times and had a nice install
now my computer keeps restarting

---

### Post by MikeM709 on 2007-06-03
computer specs please. also, did you install anything in Ubuntu that may have had an effect on the files, ect?

---

### Post by thedarkside123 on 2007-06-04
sorry :)
virtual.hard.disk = 6 gb
home = 1
swap = 0.6

i hibernated, could that have been the problem

---

### Post by MikeM709 on 2007-06-04
yes i believe theres a bug with the hibernation right now. thats most likely what your problem is. someone correct me if im wrong. this program is only in the beta stages right now so if you really like stick around and you'll be able to get it once its fully working, at least with the majority of systems.

---

### Post by thedarkside123 on 2007-06-04
do you have any suggestions on what i should do now?
my computer will not boot form the first hard drive

---

### Post by MikeM709 on 2007-06-04
i'm not sure what you need to do. what is your other operating system?

i think ecology or ago might know more about this. one of them will probably reply eventually.

---

### Post by ago on 2007-06-05
> **thedarkside123 said:**
> do you have any suggestions on what i should do now?
my computer will not boot form the first hard drive

Did you hard-reboot? That might compromise the filesystem?

use a live CD and enter the command

cat /proc/partitions

and see what partitions are visible

---

### Post by thedarkside123 on 2007-06-05
ubuntu@ubuntu:~$ cat /proc/partitions
major minor  #blocks  name

   3     0   78150744 hda
   3     1   78140128 hda1
   7     0     646072 loop0

i remember it wouldnt hibernate after an hour so i hard-rebooted
i dont have any other os s running

---

