---
title: "Shell output redirection"
date: 2013-11-28
forum: General Help
---

### Post by zDUle98 on 2013-11-28
I'm trying to measure running time of my program with this line
```
p=$(time cat input_file | ./program >> output_file)
```
I want to capture the output of time to the variable p, but the output is printed on the screen and p remains empty. Does enybody know what's the problem?

---

### Post by Lars Noodén on 2013-11-28
Which times?  Real, user or system?

If you use /usr/bin/time instead of bash's built-in time you have more options and can specify which time.  You also have to juggle with stderr, which is where time sends its output.

```

p=$(/usr/bin/time -f "%e" ./program < input_file 2>&1 >> output_file );echo $p

```

See the manual page for [time](http://manpages.ubuntu.com/manpages/saucy/en/man1/time.1.html) for the time format you choose for **-f**

---

### Post by zDUle98 on 2013-11-28
Thanks that worked

---

