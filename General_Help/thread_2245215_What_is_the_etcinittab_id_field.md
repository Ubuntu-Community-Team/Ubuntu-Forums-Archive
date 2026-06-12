---
title: "What is the /etc/inittab id field?"
date: 2014-09-21
forum: General Help
---

### Post by terminator14 on 2014-09-21
On systems that use SysV, all entries in /etc/inittab are of the form:
```
id:runlevels:action:process 
```
and the inittab man page states:
> **id** - is a unique sequence of 1-4 characters which identifies an entry in inittab (for versions of sysvinit compiled with the old libc5 (< 5.2.18) or a.out libraries the limit is 2 characters).

Note: traditionally, for getty and other login processes, the value of the id field is kept the same as the suffix of the corresponding tty, e.g. 1 for tty1. Some ancient login accounting programs might expect this, though I can't think of any. 
Those are literally the only lines (other than some examples that use it) that reference the id field in the man page. Nowhere does it say what the id field actually is - only that it "identifies an entry". Identifies entries to what? What needs to reference entries by id?

I literally changed every id field in the file to a random, unique, 2 char string, reboot the system and nothing bad happened. Making an entry with a duplicate id though gives you warnings at boot.

Why does the id field have to be unique if nothing uses it? Why is it even there?

---

### Post by yancek on 2014-09-22
/etc/inittab has not been used on Ubuntu for some time.  Take a look at the link below which has some info as well as suggestions on how to make changes and where to get info.

[http://askubuntu.com/questions/34308/where-is-inittab-file](http://askubuntu.com/questions/34308/where-is-inittab-file)

---

### Post by terminator14 on 2014-09-22
I'm aware that it is not used on Ubuntu - that's why I mentioned "On systems that use SysV". I'm not asking about Ubuntu, or upstart.
SystemV has been around since 1983, and was used by Ubuntu for many years. Someone must know what the id field was for.

---

