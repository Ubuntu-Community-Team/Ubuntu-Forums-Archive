---
title: "Most efficient way (performance wise) of chown a large amount of files (1 million+)?"
date: 2022-04-16
forum: General Help
---

### Post by Jungleboss on 2022-04-16
Hi!

What is the most efficient way (performance wise) of chown a large amount of files (1 million+) in one single directory? I don't want to burden the server more than necessary.

```
echo * | xargs chown xx:xx

find . -type f -print0 | xargs -0 chown xx:xx
```

Something else?

---

### Post by vanadium on 2022-04-17
xargs, but then with the -n option, such that it runs the chmod command fewer times with multiple arguments rather than once per single argument.

---

### Post by Holger_Gehrke on 2022-04-17
I'd use the -s or --max-chars option of xargs with an appropriate parameter to the option. 'chown' can process multiple files passed from the command line and the limit on the length of the command is quite high ('getconf MAX_ARGS' and 'xargs --show-limits' print something on the order of 2MB on my system ...). Using -s to pass as many files as will fit in one command instead of passing a fixed number of them using -n will probably be faster.

By the way, I don't think more than 1.000.000 files in a single directory is a good idea. I recall having about 10.000 files in one directory some years ago and noticing some serious slowdown when operating on anything in that directory. I can't even imagine what will happen with a million files ...

Holger

---

### Post by mIk3_08 on 2022-04-17
> **Jungleboss said:**
> Hi!
What is the most efficient way (performance wise) of chown a large amount of files (1 million+) in one single directory? I don't want to burden the server more than necessary.
```
echo * | xargs chown xx:xx
find . -type f -print0 | xargs -0 chown xx:xx
```
Something else?
This topic is something amazing. Maybe this can help to me in the near future. I want to build a multiple machine server with multi processors each. This is cool. Regards and cheers.

---

### Post by Jungleboss on 2022-04-17
Thanks! I think I'll try the -s option.
We have changed the routine for new files that is saved. They are not saved in one single directory. But these are old files that unfortunately was saved in one single dir. We can't move them because they are referenced from the application. But we have no performance problem.

---

