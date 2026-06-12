---
title: "Changing /Enlarging Swap Partition After installl?"
date: 2007-03-17
forum: General Help
---

### Post by true_friend on 2007-03-17
Hi folks
my friend just installed kubuntu edgy. installation was ok (by default) installation but he is facing problem of slow system i guess it is due to low swap which would be 256 mb by default(256 mb RAM). i think it should be 1 gb ( as i read at many places) so can some one guide me how swap partition can be increased or enhanced?
Regards
True_Friend

---

### Post by peabody on 2007-03-17
Before you rule that swap is the problem, you should probably double check to see if that's truly the cause.

Run top in a terminal when the machine is particularly slow and see how much of the swap is used.  If it's nearly full, then swap is potentially a problem.  If it's not, then it could be related to something else.

---

### Post by true_friend on 2007-03-17
plz give me command to check memory status through terminal or through ksysgurad?

---

### Post by peabody on 2007-03-17
The command is called "top".  I mentioned it in my previous post, but I could see how it was easy to miss.

The "free" command also works, and to my knowledge, all graphical system monitors should have some option to view used swap.

---

### Post by patrickthebold on 2007-03-17
If it is swap, and you don't want to repartition you can use a swap file.  Its a new install so the easiest thing would probably be to just reinstall with a bigger swap partition, but the overall easiest thing to do would be to just add a swap file.

---

### Post by true_friend on 2007-03-18
and how to add a swap file?

---

### Post by true_friend on 2007-03-18
This is the "Top" output memory is fully used and swap is not
----------------------------------------------------------------------
top - 15:42:17 up  4:06,  1 user,  load average: 2.36, 1.50, 1.29
Tasks:  97 total,  2 running,  94 sleeping,  0 stopped,  1 zombie
Cpu(s): 60.6%us,  3.6%sy,  0.0%ni, 35.8%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:    254900k total,  250704k used,    4196k free,    5280k buffers
Swap:  738948k total,  107940k used,  631008k free,    92176k cached
-------------------------------------------------------------------------
any ideas???

---

### Post by peabody on 2007-03-18
I really doubt it's swap, there seems to be plenty to go 'round.  Is there a particular activity that seems to make the machine slow?  That it's slow at doing?

---

### Post by true_friend on 2007-03-18
i am also in doubt. i think it is due to processor (800 MHZ only)
KDE is too large for this speed i think.

---

### Post by peabody on 2007-03-18
That's only true if CPU usage is constantly high.  Use a system monitor to view the cpu usage through day to day activities.  If its plastered at 100% almost all of the time, that could be the case, although it's worth looking into what's causing that.  Could be video drivers or something else.

---

