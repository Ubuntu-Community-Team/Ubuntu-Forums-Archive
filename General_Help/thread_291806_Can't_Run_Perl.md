---
title: "Can't Run Perl"
date: 2006-11-03
forum: General Help
---

### Post by ericinwisconsin on 2006-11-03
From the command prompt, as root, I can't run perl.

root@eric:~# perl

and the system just hangs.

Any idea on this one, guys?

---

### Post by po0f on 2006-11-03
ericinwisconsin,

Perl isn't as awesome as Python, and doesn't come with an interactive interpreter (at least by default, there might be one out there).  You'll have to put your Perl scripts in a file and run them that way, or execute the script directly on the command line:
```
$ perl -e 'print "hello world!"'
```
Yuck.

---

### Post by ericinwisconsin on 2006-11-07
No interpreter??? Sheesh!

Ubuntu just went down from A+ to B- in my book.

---

### Post by taurus on 2006-11-07
> **ericinwisconsin said:**
> No interpreter??? Sheesh!

Ubuntu just went down from A+ to B- in my book.
If you don't have perl on your system, just install it!!!  :rolleyes: 

```
sudo aptitude update
sudo aptitude install perl
```

---

### Post by po0f on 2006-11-07
ericinwisconsin,

Ubuntu doesn't have an *interactive* interpreter, the Perl binary itself is the interpreter.  Anyway, I doubt any Linux distro ships with an interactive Perl interpreter, if one even exists.

If you want to try out a new programming language, try [Python](http://www.python.org/).  It comes installed by default on Ubuntu, and most other Linux distributions for that matter.

---

### Post by fragos on 2006-11-07
> **ericinwisconsin said:**
> No interpreter??? Sheesh!

Ubuntu just went down from A+ to B- in my book.

I suggest you do a little research before you badmouth anything.  What you're complaining about doesn't have anything to do with Ubuntu and for that matter isn't even correct.  Perl is an interpreter.  If you read any documentation you'd see that Perl Code is identified by the 1st line of the program file.  Same goes for bash.

---

