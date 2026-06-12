---
title: "bash symbolic links"
date: 2007-04-28
forum: General Help
---

### Post by koara on 2007-04-28
Hello, simple newbie question, but i was unable to find the answer:

After creating a symbolic link to a directory (~$ ln -s A/B C), i follow the link (~$ cd C). How do i force the shell to think of C as ~/A/B again, instead of ~/C? For example, so that ```
~/C$ cd ..
``` gets me to ~/A, instead of to ~? In other words, forget how i got there, and treat the current directory as though it was accessed by typing out its full path?

Cheers!

GNU bash, version 3.2.13(1)-release-(i486-pc-linux-gnu)

---

### Post by stylishpants on 2007-04-28
You need the "-P" flag of the "cd" command.

```
fraser@ged:/tmp$ help cd
cd: cd [-L|-P] [dir]
    Change the current directory to DIR.  The variable $HOME is the
    default DIR.  The variable CDPATH defines the search path for
    the directory containing DIR.  Alternative directory names in CDPATH
    are separated by a colon (:).  A null directory name is the same as
    the current directory, i.e. `.'.  If DIR begins with a slash (/),
    then CDPATH is not used.  If the directory is not found, and the
    shell option `cdable_vars' is set, then try the word as a variable
    name.  If that variable has a value, then cd to the value of that
    variable.  The -P option says to use the physical directory structure
    instead of following symbolic links; the -L option forces symbolic links
    to be followed.
fraser@ged:/tmp$ mkdir -p A/B
fraser@ged:/tmp$ ln -s A/B C
fraser@ged:/tmp$ cd C
fraser@ged:/tmp/C$ cd -P ..
fraser@ged:/tmp/A$ 

```

---

### Post by koara on 2007-05-04
stylishpants, thanks! 
exactly the simple answer i was looking for.

in case anyone else finds this useful, try adding
```

alias cdp='cd -P'

``` 
to ~/.bashrc for convenience

---

### Post by jnorthr on 2007-07-02
Can't figure this out yet in ubuntu 7.0.4 : how do i list my symbolic links and how do i delete a sym link if i need to ?
ta

---

### Post by bodhi.zazen on 2007-07-02
List them with : ls -l

remove them with :  unlink <link>

---

