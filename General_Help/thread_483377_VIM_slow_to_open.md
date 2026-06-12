---
title: "VIM slow to open"
date: 2007-06-24
forum: General Help
---

### Post by userundefine on 2007-06-24
userundefine@nomadsland:~$ time vim test
real    0m8.348s
user    0m0.056s
sys     0m0.016s

I've removed my .viminfo and .vimrc to no avail.  Still very slow to open, but not to function once it is open.  Not sure how to fix this...

---

### Post by sumanc on 2007-11-29
I am having same problem for Ubuntu 7.10 in Dell Inspiron 1420 with complete updates.

Not only vim/gvim, other programs like emacs is also slow to open. But some graphics programs like xmgrace opens rather fast! I am confused. Any guideline will be highly appreciated! :)


--Suman.

---

### Post by hugmenot on 2007-11-29
How is it when you start with

time vim -u NONE -U NONE -c q

That also avoids loading system defaults.

---

### Post by mw44118 on 2008-02-18
I'm having the same problem.

It seems to be related to which terminal I use.  If I use xterm, I have to wait 6 seconds.

If I use the gnome terminal, I get vi instantaneously.

Maybe there is something wrong with my xterm settings.

---

### Post by jgmize on 2008-05-22
I had the same problem with a slow vim start after I upgraded to 8.04. Using the "-X" argument, which tells vim not to connect to the X server, fixed the problem for me, so I modified my .bash_aliases file to include that argument by default.

---

### Post by jiangxin on 2008-07-14
I have the same problem. 

```
$ time vim -u NONE -U NONE -c q
real    0m6.222s
user    0m0.128s
sys     0m0.044s

```

Do a strace, I find a clue:
```

$ strace vim -q
...
connect(6, {sa_family=AF_FILE, path="/tmp/.ICE-unix/8030"}, 21) = -1 ENOENT (No such file or directory)
...
connect(6, {sa_family=AF_FILE, path="/tmp/.ICE-unix/8030"}, 21) = -1 ENOENT (No such file or directory)
...
connect(6, {sa_family=AF_FILE, path="/tmp/.ICE-unix/8030"}, 21) = -1 ENOENT (No such file or directory)
...
...repeated 6 times total, waste 6 seconds 

```

X-windows session file what vim looking for is not exist.
```
$ cd /tmp/.ICE-unix
$ ln -s some-exists-file  8030
$ time vim -u NONE -U NONE -c q
real    0m0.186s
user    0m0.132s
sys     0m0.044s
```

Or, simply using the "-X" argument not connect to X-server.
$ vim -X

---

### Post by ChameleonDave on 2008-07-14
Interesting.  I have a fresh Hardy installation, and it is instantaneous for me in both Yakuake and xterm.

---

