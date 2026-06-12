---
title: "Problem to grep/cut/awk output from perf tool"
date: 2012-11-14
forum: General Help
---

### Post by Kdar on 2012-11-14
I am trying to run perf stat command like this (command with it's output):
```
armend@eb136i-t1600:~/run-parsec$ perf stat -x' ' -r 5 -e cycles,cpu-clock ls
black1.txt  black2.txt  blackholes.likwid.txt  cm.sh  file
black1.txt  black2.txt  blackholes.likwid.txt  cm.sh  file
black1.txt  black2.txt  blackholes.likwid.txt  cm.sh  file
black1.txt  black2.txt  blackholes.likwid.txt  cm.sh  file
black1.txt  black2.txt  blackholes.likwid.txt  cm.sh  file
2017706 cycles 0.61%
1.265934 cpu-clock 0.63%
```

However, if I try to pipe grep or awk or cut it doesn't filter the last two lines I am interested in, if filters everything above.

For example:
```
armend@eb136i-t1600:~/run-parsec$ perf stat -x' ' -r 5 -e cycles,cpu-clock ls | grep 'black'
**black**1.txt
**black**2.txt
.
.
.
**black**1.txt
**black**2.txt
blackholes.likwid.txt
1978041 cycles 0.44%
1.238484 cpu-clock 0.44%
```

But if I do something like what I really want to filter, I get this nothing. I only get two last lines:
```
2017706 cycles 0.61%
1.265934 cpu-clock 0.63%
```

And I am interested in filtering output in those two last lines, not output of "ls". How can I force it to filter output of actual perf stat?

---

### Post by sisco311 on 2012-11-14
By default, `pref stat' prints its output to stderr. Check out BashFAQ 047 (link in my signature).

EDIT: I don't see it mentioned in the FAQ, so I would like to add that **|&** in bash is a shorthand for **2>&1 |**. You might find it handy in an interactive shell. It's a bashism; you probably should avoid it in scripts...

---

### Post by Kdar on 2012-11-14
I tried to use 2>&1 | as well, but it had same results.

The thing is, it works for me on other Linux machine, but not in Ubuntu 12.04.

On other machine I run following command:
(perf stat -x' ' -r 5 -e cycles,cpu-clock ls) 2>&1 | grep 'cycles

But in Ubuntu 12.04 this doesn't work.

---

### Post by sisco311 on 2012-11-14
What do you mean by it doesn't work?

If you simply want to print the cycles line, why don't you run something like:
```
perf stat -x' ' -r 5 -e cycles  ls > /dev/null
```?

---

