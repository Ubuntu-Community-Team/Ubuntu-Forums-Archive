---
title: "What version am I on?"
date: 2007-04-20
forum: General Help
---

### Post by jds8 on 2007-04-20
dmesg|grep "Linux version" returns:

 Linux version 2.6.15-28-386 (buildd@terranova) (gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)) #1 PREEMPT Thu Feb 1 15:51:56 UTC 2007

Also, I went to a site that said all you had to do to find out your version was type: 

cat/proc/version

at the command line, but this didn't work, did I miss something?

---

### Post by Famicommie on 2007-04-20
it's ```
cat /proc/version
```
You need a space between 'cat' and '/proc'.

---

### Post by stylishpants on 2007-04-20
```
fhanson@fhanson:~$ cat /proc/version
Linux version 2.6.20-15-386 (root@palmer) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 Sun Apr 15 07:34:00 UTC 2007

```

Don't be confused by this.  This gives you your Linux kernel version, and the version of the compiler that built that kernel.  It does not give you the version of Ubuntu you currently have installed (although you can figure that out from this if you're keen.)

Here are 2 ways to find out what version of Ubuntu you have:

1.  cat /etc/issue
```

fhanson@fhanson:~$ cat /etc/issue
Ubuntu 7.04 \n \l

```

2. In the "System" menu, choose "About Ubuntu".  The first page that appears should have both the release number (eg. 7.04) and the release name (eg. "Feisty Fawn").

---

### Post by Gavin77 on 2007-04-20
This should work

```
lsb_release -a
```

---

### Post by jds8 on 2007-04-21
Thanks!

---

