---
title: "how do i own a disowned process"
date: 2008-05-29
forum: General Help
---

### Post by spice_vs on 2008-05-29
hi,
i am in a fix.
i got a big process to run
could start screen (sorry for that) 
so to disown it i did the following.
$>mysql -uuser1 < abc.sql
^Z
$>disown
bash: warning: deleting stopped job 1 with process group 16770

now it is in stopped state and a big trouble.
how do i own back the process. please help .

thanks
spice

---

### Post by hyperair on 2008-05-29
I don't think it's possible, but maybe I just don't know enough.

---

### Post by bingoUV on 2008-05-29
Don't know about owning, but you could always cause it to continue in the disowned state. Send a SIGCONT signal to it
```

kill -s SIGCONT <pid>

```

---

### Post by spice_vs on 2008-05-29
kill -s SIGCONT <pid>

Doesn't start the process disowned by me.

$ ps u | grep 'mysql -u'
kganesh  18844  0.0  0.2  9492 2248 pts/6    T    21:49   0:00 mysql -uyahoo -px xxxxx -hkganesh-dt.eglbp.corp.yahoo.com
kganesh  18910  0.0  0.0  4700  644 pts/6    S+   21:52   0:00 grep mysql -u
$ kill -s SIGCONT 18844
$ ps u | grep 'mysql -u'
kganesh  18844  0.0  0.2  9492 2248 pts/6    T    21:49   0:00 mysql -uyahoo -px xxxxx -hkganesh-dt.eglbp.corp.yahoo.com
kganesh  18912  0.0  0.0  3824  644 pts/6    S+   21:52   0:00 grep mysql -u

---

### Post by niteshifter on 2008-05-29
Hi,

Try:

```
sudo /bin/kill -s SIGCONT <pid>
```

Note: there are two kills in a system. The built in bash job control command (which is what you've been using) and the system binary. I'm thinking bash is possibly getting in your way here.

---

### Post by bingoUV on 2008-05-29
> **spice_vs said:**
> kill -s SIGCONT <pid>

Doesn't start the process disowned by me.

$ ps u | grep 'mysql -u'
kganesh  18844  0.0  0.2  9492 2248 pts/6    T    21:49   0:00 mysql -uyahoo -px xxxxx -hkganesh-dt.eglbp.corp.yahoo.com
kganesh  18910  0.0  0.0  4700  644 pts/6    S+   21:52   0:00 grep mysql -u
$ kill -s SIGCONT 18844
$ ps u | grep 'mysql -u'
kganesh  18844  0.0  0.2  9492 2248 pts/6    T    21:49   0:00 mysql -uyahoo -px xxxxx -hkganesh-dt.eglbp.corp.yahoo.com
kganesh  18912  0.0  0.0  3824  644 pts/6    S+   21:52   0:00 grep mysql -u

For me it is doing perfectly fine. Can you show the output of 
```

which kill

```

---

### Post by spice_vs on 2008-05-30
hi the kill is /bin/kill only. 

```

[kganesh ~]$ which kill
/bin/kill
[kganesh ~]$

```

---

### Post by sdennie on 2008-05-30
Doing one of the two things always works fine for me:

```

nohup some_program > /dev/null

```

(Close parent shell however you see fit)

```

some_program
^Z
bg
disown
exit

```

(Note the bg)

Or, you can also use screen to accomplish something like this.

Note: Looking closer at the original post, are you sure you don't need to just type: "bg" or "fg"?

---

