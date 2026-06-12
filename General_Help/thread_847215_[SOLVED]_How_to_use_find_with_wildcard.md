---
title: "[SOLVED] How to use find with wildcard"
date: 2008-07-02
forum: General Help
---

### Post by Titan8990 on 2008-07-02
I am trying to find a file that is going to end in .ldif. When I use the following command it returns an error:

$jordan@einstein:/root$ find / -name *.ldif
find: paths must precede expression
Usage: find [-H] [-L] [-P] [path...] [expression]


It appears that my syntax is correct according to the usage listed there as well as find man pages. I can end a find search in a wildcard but can not start one.

So what is the correct syntax for finding a file that ends in .ldif?

---

### Post by Titan8990 on 2008-07-02
Alright, I looked trough the man pages more thoroughly and I was able to solve my problem. If anyone else is looking for an answer to this problem here was the solution:

root@einstein:~# find / -name '*.ldif'

The expression that begins with a wildcard must be put in single quotes. Here is the excerpt from the find man page:

 ```
$ find . -name *.c -print
       find: paths must precede expression
       Usage: find [-H] [-L] [-P] [path...] [expression]

       This happens because *.c has been expanded by the  shell  resulting  in
       find actually receiving a command line like this:

       find . -name bigram.c code.c frcode.c locate.c -print

       That  command  is of course not going to work.  Instead of doing things
       this way, you should enclose the pattern in quotes:
       $ find . -name ´*.c´ -print
```

---

### Post by ghostdog74 on 2008-07-02
a good habit: try to use quotes every time
```

# find /path -name "*.ldif"

```

---

### Post by drs305 on 2008-07-02
Just personal technique, but instead of "-name" you can substitute "-iname" to make the search case INsensitive. It's only typing one extra letter but may yield much better results if you aren't sure of the capitalization.

---

